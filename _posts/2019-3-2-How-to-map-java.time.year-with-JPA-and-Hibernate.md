---
layout: post
date: 2019-5-3
title: How to map java.time.year with JPA and Hibernate 
excerpt_separator: <!--more-->
---
                                                                                                              
Greetings!
<!--more-->

JPA 2.2 and Hibernate support several classes of the Date and Time API. Unfortunately, the *java.time.Year* class isn’t one of them. If you want to use it as an attribute type, you need to provide a custom mapping for it.

But don’t worry, you can do that easily with an [AttributeConverter](https://thoughts-on-java.org/jpa-21-how-to-implement-type-converter/), and it only requires a few lines of code.

An AttributeConverter provides a portable way to create custom type mappings. The only thing you need to do is to implement the *AttributeConverter* interface and annotate your class with the *@Converter* annotation.

Implementing the YearConverter
---

Here you can see an example of an AttributeConverter that maps a *java.time.Year* object to a Short.

```
@Converter(autoApply = true)
public class YearConverter implements AttributeConverter<Year, Short> {
     
    Logger log = Logger.getLogger(YearConverter.class.getSimpleName());
 
    @Override
    public Short convertToDatabaseColumn(Year attribute) {
        short year = (short) attribute.getValue();
        log.info("Convert Year ["+attribute+"] to short ["+year+"]");
        return year;
    }
 
    @Override
    public Year convertToEntityAttribute(Short dbValue) {
        Year year = Year.of(dbValue);
        log.info("Convert Short ["+dbValue+"] to Year ["+year+"]");
        return year;
    }
}
```

As you can see, the implementation of a converter is very simple. The interface only defines a method to convert the entity attribute to its database representation and another one for the inverse operation.

In this example, the implementation of these 2 methods is pretty simple because the *Year* class already provides methods to get the *Integer* value of a give *Year* object and to create a *Year* object from an *Integer*. You can then either persist the *Integer* or you can try to save some space and cast it to a *Short*.

When you annotate your *AttributeConverter* with the *@Converter* annotation, you should ask yourself if you want to use it for all attributes of the converted type. If you want to do that, you should set the *autoApply* attribute to *true*. Hibernate will then use the converter automatically, and you don’t need to use any additional mapping annotation. In this case, the decision is easy. Hibernate doesn’t support *java.time.Year* as a type and you should use it for all entity attributes of that type.

Using the YearConverter
---

After you implemented the YearConverter and added it to your project, you can use *java.time.Year* as an attribute type. And because you set the *autoApply* attribute to true, you can do that without any additional mapping annotations.

```
@Entity
public class OnlineCourse {
 
    @Id
    @GeneratedValue
    private Long id;
 
    private String title;
 
    private Year publishingYear;
 
    @Version
    private long version;
 
    ...
}
```

That's it, If you're looking for more tips on Java and Hibernate you can check [Thoughts on Java](https://thoughts-on-java.org)

Thank you, regards. 
