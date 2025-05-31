# Getting Started

**It only takes five steps to go from initialization to connection!**

1. Add AxolotlDev Repository

**Add the private repository**

<tabs>
  <tab title="Maven">
    <code-block lang="XML"><![CDATA[
      <repositories>
        <repository>
          <id>axolotldev-repo</id>
          <url>https://repo.axolotldev.me/repository/maven-public/</url>
        </repository>
      </repositories>
    ]]></code-block>
  </tab>
  <tab title="Gradle (Groovy DSL)">
    <code-block lang="Gradle">
        repositories {
            maven {
                url "https://repo.axolotldev.me/repository/maven-public/"
            }
        }
    </code-block>
  </tab>
  <tab title="Gradle Kotlin DSL">
    <code-block lang="Kotlin">
        repositories {
            maven {
                url = uri("https://repo.axolotldev.me/repository/maven-public/")
            }
        }
    </code-block>
  </tab>
</tabs>

2. Load the Core Component

![Current Version for Core library](https://img.shields.io/nexus/r/me.axolotldev.dbconnector/Core?server=https%3A%2F%2Frepo.axolotldev.me%2F&label=Current%20Version)

<tabs>
  <tab title="Maven">
    <code-block lang="XML"><![CDATA[
        <dependency>
            <groupId>me.axolotldev.dbconnector</groupId>
            <artifactId>Core</artifactId>
            <version>x.y.z</version>
        </dependency>
    ]]></code-block>
  </tab>
  <tab title="Gradle (Groovy DSL)">
    <code-block lang="Gradle">implementation 'me.axolotldev.dbconnector:Core:x.y.z@jar'</code-block>
  </tab>
  <tab title="Gradle Kotlin DSL">
    <code-block lang="Kotlin">implementation("me.axolotldev.dbconnector:Core:x.y.z@jar")</code-block>
  </tab>
</tabs>

3. Choose the Appropriate Database Connector

Please refer to the [available database drivers](version.md#database-drivers).

<tabs>
  <tab title="Maven">
    <code-block lang="XML"><![CDATA[
        <dependency>
            <groupId>me.axolotldev.dbconnector</groupId>
            <artifactId>xxxDriver</artifactId>
            <version>x.y.z</version>
        </dependency>
    ]]></code-block>
  </tab>
  <tab title="Gradle (Groovy DSL)">
    <code-block lang="Gradle">implementation 'me.axolotldev.dbconnector:xxxDriver:x.y.z@jar'</code-block>
  </tab>
  <tab title="Gradle Kotlin DSL">
    <code-block lang="Kotlin">implementation("me.axolotldev.dbconnector:xxxDriver:x.y.z@jar")</code-block>
  </tab>
</tabs>

4. Create a Database Connection

<tabs>
  <tab title="Java">
    <code-block lang="Java"><![CDATA[
        import me.axolotldev.dbc.core.connect.ConnectBuilder;
        import me.axolotldev.dbc.abstracts.database.DatabaseInfo;
        import me.axolotldev.dbconnector.driver.xxxDriverData;
        import me.axolotldev.dbc.abstracts.database.Connector;
        
        import java.util.HashMap;
        import java.util.Map;
        import java.util.Properties;
        
        public class DatabaseConnection {
            public static void main(String[] args) {
        
                // Set URI options (e.g., SSL, timezone, etc.)
                final Map<String, String> options = new HashMap<>();
                options.put("ssl", "true");
                // Add other parameters as needed
            
                // Create the database connection info
                final DatabaseInfo dbInfo = new DatabaseInfo(
                        "127.0.0.1",     // URI
                        3306,            // Port
                        "root",          // Username
                        "password",      // Password (will be securely handled)
                        "my_database",   // Database name
                        options          // Connection options
                );
            
                // Set internal behavior properties (optional)
                final Properties meta = new Properties();
                meta.put("autoReconnect", "true");
                // Add more custom settings if needed
            
                // Create the database connection
                final Connector connector = new ConnectBuilder(
                        dbInfo,
                        xxxDriverData.INSTANCE,
                        meta
                ).build();
            
                // Now you can use the connector for operations
            }
        }
]]>
</code-block>
  </tab>
  <tab title="Kotlin">
    <code-block lang="Kotlin"><![CDATA[
        import me.axolotldev.dbc.core.connect.ConnectBuilder
        import me.axolotldev.dbc.abstracts.database.DatabaseInfo
        import me.axolotldev.dbconnector.driver.xxxDriverData
        import me.axolotldev.dbc.abstracts.database.Connector
        
        fun main() {
        // Create the database connection info and internal properties in one step
        val connector = ConnectBuilder(
        DatabaseInfo(
        "127.0.0.1",     // URI
        3306,            // Port
        "root",          // Username
        "password",      // Password (will be securely handled)
        "my_database",   // Database name
        mapOf("ssl" to "true") // Connection options
        ),
        xxxDriverData.INSTANCE,
        Properties().apply { put("autoReconnect", "true") }  // Internal behavior properties
        ).build()
        
            // Now you can use the connector for operations
        }
]]>
</code-block>
  </tab>
</tabs>


5. Connection Complete!

**Now you can use the connector to execute queries, transactions, and encapsulate logic, etc.!**