# Liquibase MaxDB Extension 

This is a Liquibase extension for MaxDB support.

[SAP® MaxDB™](https://maxdb.sap.com/) is the database management system developed and supported by SAP SE. SAP MaxDB is available on Microsoft Windows, Linux and Unix, and for the most prominent hardware platforms.

## Configuring the extension

These instructions will help you make the extension up and running on your local machine for development and testing purposes.

### Liquibase CLI

Download [the latest released Liquibase extension](https://github.com/liquibase/liquibase-maxdb/releases) `.jar` file and place it in the `Liquibase/lib` install directory. If you want to use another location, specify the extension `.jar` file in the `classpath` of your [liquibase.properties file](https://docs.liquibase.com/workflows/liquibase-community/creating-config-properties.html).

### Maven
Specify the Liquibase extension in the `<dependency>` section of your POM file by adding the `org.liquibase.ext` dependency for the Liquibase plugin. 
 
```  
<plugin>
     <!--start with basic information to get Liquibase plugin:
     include <groupId>, <artifactID>, and <version> elements-->
     <groupId>org.liquibase</groupId>
     <artifactId>liquibase-maven-plugin</artifactId>
     <version>4.2.0</version>
     <configuration>
        <!--set values for Liquibase properties and settings
        for example, the location of a properties file to use-->
        <propertyFile>liquibase.properties</propertyFile>
     </configuration>
     <dependencies>
     <!--set up any dependencies for Liquibase to function in your
     environment for example, a database-specific plugin-->
            <dependency>
                 <groupId>org.liquibase.ext</groupId>
                 <artifactId>liquibase-maxdb</artifactId>
                 <version>${liquibase-maxdb.version}</version>
            </dependency>
         </dependencies>
      </plugin>
  ``` 
  
## Java call
  
```
public class Application {
    public static void main(String[] args) {
        MaxDBDatabase database = (MaxDBDatabase) DatabaseFactory.getInstance().openDatabase(url, null, null, null, null);
        Liquibase liquibase = new Liquibase("liquibase/ext/changelog.generic.test.xml", new ClassLoaderResourceAccessor(), database);
        liquibase.update("");
    }
}
```
## Contribution

To file a bug, improve documentation, or contribute code, follow our [guidelines for contributing](https://www.liquibase.org/community). 

[This step-by-step instructions](https://www.liquibase.org/community/contribute/code) will help you contribute code for the extension. 

Once you have created a PR for this extension you can find the artifact for your build using the following link: [https://github.com/liquibase/liquibase-maxdb/actions/workflows/build.yml](https://github.com/liquibase/liquibase-maxdb/actions/workflows/build.yml).

## Documentation

[Using Liquibase with MaxDB](https://docs.liquibase.com/workflows/database-setup-tutorials/maxdb.html)

## License

This project is licensed under the [Apache License Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).
