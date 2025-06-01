# Available Metadata

**These metadata options can be used to control the behavior of DBConnector, allowing you to adjust logic based on your needs.**

> All items are optional
>
{style="note"}

| id            | Description                                                                                                                                                                                   | Default |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| autoReconnect | Whether to automatically reconnect when the database connection is lost.                                                                                                                      | false   |
| retryTimes    | Number of retry attempts if the connection fails. If it still fails, a [SQLException](https://docs.oracle.com/en/java/javase/21/docs/api/java.sql/java/sql/SQLException.html) will be thrown. | 1       |
