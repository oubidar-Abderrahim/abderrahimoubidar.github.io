---
layout: post
date: 2018-1-19
title: Create a Voice Command App with Java and Sphinx4!
---

Greetings!

In this tutorial, We are going to build a *Voice Command App* using *Sphinx4 Speech Recognition Library* with *Java*. 

I read an article on _Procurity's blog_ about it, and it made me want to try it myself! which I did, but i had some issues that i tried to solve. So i hope if you are curious too that the code below will work perfectly for you!

Our app will be able to listen and understand 5 simple commands and execute them in a windows machine. for Linux and Mac Os users, you need to update the commands to match you're operating system's commands.
the commands that we are using are : 
- Open file Manager : will open a new window of your file manager. 
- close file Manager : will close *All* opened windows of your file manager.
- Open browser : will open firefox in my case (you can open any browser you want, just specify its location).
- Close browser : will close firefox.
- Exit program : to end the program.

Here is a link to the original post : [Make your own Voice Command App using Java and Sphinx4](https://procurity.wordpress.com/2016/09/10/make-your-own-voice-command-app-using-java-and-sphinx4/ "Make your own Voice Command App using Java and Sphinx4") 

##Requirements :

Before starting here is what you are going to need:
- Obviously, an IDE with Jdk installed (preferably Java 8 or above)
- For this tutorial we're going to use maven to download the necessary Jars but you can get them if you wish directly from [Sphinx4](https://cmusphinx.github.io/wiki/download/ "Sphinx4")  
- A working Microphone
*Note* I am using Windows 10 as my OS.

##About Models
There are basically three models required for speech recognition in Sphinx4:

Acoustic Model
Phonetic Dictionary (File ends with .dict extension)
Language Model (File ends with .lm extension)
The sphinx4-data.jar comes with the English version of Acoustic Model as Default hence we will be using that, if you are using other language then you’ll have to download it from [Here](https://sourceforge.net/projects/cmusphinx/files/Acoustic%20and%20Language%20Models/).

Since we are creating a Voice Command app so we’ll be creating our own Language Model and the Phonetic Dictionary because our vocabulary will be limited i.e. our commands only. Now lets create our needed files :

##Creating Language Model & Dictionary
As said above our vocabulary is limited hence making the model and dict will be a breeze thanks to Sphinx Online Base Generator. But first we have to make a corpus (Data using which we will train our Language Model) file containing our commands for which we will create our Language Model and Dictionary. For this tutorial I’ll be choosing 5 commands.

open file manager
open browser
close browser
close file manager
exit program

Now type these commands in your text file and save it. Then navigate to the [Sphinx Online Base Generator](http://www.speech.cs.cmu.edu/tools/lmtool-new.html "Sphinx Online Base Generator"), click *Choose File* and select your corpus text file. Now in response the site will give you a list of files, for now we are interested in the files ending with *.dict* and *.lm* extension, so download them.

##Creating the App

Create a new project (if you're familiar with maven use it, if not a simple Java project will work just fine)
Now add the dependencies for [Sphinx4-core](https://mvnrepository.com/artifact/de.sciss/sphinx4-core/1.0.0 "Sphinx4-core") and [Sphinx4-data](https://mvnrepository.com/artifact/de.sciss/sphinx4-data/1.0.0 "Sphinx4-data") to your POM.xml, or add the jars to your build path
then place the *.dict* and *.lm* in your resources folder

Once done with that, you're ready to write some code!!
*Note* the code is commented to help you understand it better.

```java
import edu.cmu.sphinx.api.Configuration;
import edu.cmu.sphinx.api.LiveSpeechRecognizer;
import edu.cmu.sphinx.api.SpeechResult;
import java.io.IOException;
import java.util.concurrent.TimeUnit;

/**
 *
 * @author Abderrahim OUBIDAR
 */
 
public class VoiceLauncher {
  public static void main(String[] args) throws IOException {
    
    // Configuration Object
    Configuration configuration = new Configuration();

    // Set path to the acoustic model.
    configuration.setAcousticModelPath("resource:/edu/cmu/sphinx/models/en-us/en-us");
    
    // Set path to the dictionary.
    String DICTIONARY_PATH = VoiceLauncher.class.getResource("/2457.dic").toString();
    configuration.setDictionaryPath(DICTIONARY_PATH);
    
    // Set path to the language model.
    String LANGUAGE_MODEL_PATH = VoiceLauncher.class.getResource("/2457.lm").toString();
    configuration.setLanguageModelPath(LANGUAGE_MODEL_PATH);

    // Recognizer Object, Pass the Configuration object
    LiveSpeechRecognizer recognize = new LiveSpeechRecognizer(configuration);

    // Start Recognition Process (The boolean parameter clears the previous cache if true)
    recognize.startRecognition(true);

    // Create SpeechResult Object
    SpeechResult result;
    
    // create process to start explorer.exe
    ProcessBuilder explorerProcess = new ProcessBuilder("explorer.exe");
    
    // create process to kill explorer
    ProcessBuilder killExplorerProcess = new ProcessBuilder("taskkill", "/f", "/im", "explorer.exe");
    
    // create process to kill explorer
    ProcessBuilder firefoxProcess = new ProcessBuilder("C:\\Program Files\\Mozilla Firefox\\firefox.exe");    
    
    // create process to kill explorer
    ProcessBuilder killFirefoxProcess = new ProcessBuilder("taskkill", "/f", "/im", "firefox.exe"); 

    // Checking if recognizer has recognized the speech
    while ((result = recognize.getResult()) != null) {
     
      // Get the recognize speech
      String command = result.getHypothesis();
      
      //Match recognized speech with our commands
      if(command.equalsIgnoreCase("open file manager")) {
        
        // execute the process
        explorerProcess.start() ;
          
        System.out.println("File Manager Opened!");

      } else if (command.equalsIgnoreCase("close file manager")) {
        
        killExplorerProcess.start();

        System.out.println("File Manager Closed!");
          
        // wait a second so finish executing the taskkill (it need's a moment to empty the cache)
        try {
          TimeUnit.SECONDS.sleep(1);
        }catch(InterruptedException e) {}

        // restart explorer, otherwise your desktop will be gone
        explorerProcess.start();
          
      } else if (command.equalsIgnoreCase("open browser")) {
          
        // open firefox, that should take a few seconds
        firefoxProcess.start() ;
        
        System.out.println("FireFox Opened!");
      } else if (command.equalsIgnoreCase("close browser")) {
        
        killFirefoxProcess.start() ;
        
        System.out.println("FireFox Closed!");
        
      } else if (command.equalsIgnoreCase("exit program")) {
        System.out.println("Exiting Program! Bye!");
        break;
      }
    }
  }
}
```

##Adding more commands
In order to add more commands, just add your new commands in your previous *txt file* and then repeat the steps from the *Creating Language Model and Dictionary*.

*The Code in Github :* [Create a Voice Command App with Java and Sphinx4](https://github.com/oubidar-Abderrahim/MyJavaWork/tree/master/VocalCommand "Github")

That it! I hope everything was clear and have fun with you're new cool voice command app 

Thank you, regards.
