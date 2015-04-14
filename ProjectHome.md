<font color='green'>Again: sorry for late! But is here now.</font>

# Maven Replacer Plugin #

This plugin replace some values indicated in pom.xml for others. It's a copy of http://code.google.com/p/maven-replacer-plugin, to improve some limitations.

## Default Substitutes ##
| **REPLACER** | **Mean** |
|:-------------|:---------|
| @PROJECT\_VERSION@ | Project pom.xml version (same as ${project.version})  |
| @VERSION\_SCM@ | Project last scm version |
| @DATE\_TIME@ | Timestamp with default java format |

Put 

&lt;datePattern&gt;



&lt;/datePattern&gt;

 in configuration section plugin to modify the format of @DATE\_TIME@.

## Custom Substitutes ##
You may put any string to be replaced. You may have to substitute for any project maven variable, like ${project.inceptionYear}. See in section "Cool Things".

## Repo ##
Yeah!!! We have repo things. Put in your project:
```
  <pluginRepositories>
    <pluginRepository>
      <id>Google Code Maven Substitute Repository</id>
      <url>http://maven-substitute-plugin.googlecode.com/svn/release-repo</url>
      <snapshots>
        <enabled>false</enabled>
      </snapshots>
      <releases>
        <enabled>true</enabled>
      </releases>
    </pluginRepository>
  </pluginRepositories>
```

## Cool Things ##
You do cool thinks like that:

```
<plugin>
  <groupId>com.google.maven-substitute-plugin</groupId>
  <artifactId>maven-substitute-plugin</artifactId>
  <version>0.2</version>
  <executions>
    <execution>
      <goals>
        <goal>replace</goal>
      </goals>
      <configuration>
        <includes>
          <include>/target/**/*_jsp.java</include>
        </includes>
        <excludes>
          <exclude>/target/**/Invoice*.java
        </excludes>
        <token>@NAME@</token>
        <value>${project.name}</value>
        <fail>false</fail>
      </configuration>
    </execution>
  </executions>
</plugin>
```

## Fast Resume ##
As you can see, put included and excluded files like ant wildcards to substitute words in your project.

## Some Words About ##
This typical usage in codehaus jspc mojo compiler includes any file in directory "target" finished by "_jsp.java" and excludes any file in same directory initiating by "Invoice" and terminating in ".java". Note which the process don't fail when no file is found, because the directive "fail" is set to "false". Note which this is not a default behavior, which is "true"._

## More "BLAH BLAH" ##
The default phase attached is "process-sources", because when jspc compile, generate sources (servlets) and then compile to final classes. This behavior is convenient to others environments too.

## Final Thinks ##
If you like, put 

&lt;phase&gt;

 in this configuration and you will have this convenience attached to another phase.


If the author of the plugin like contact me to unify both! :)