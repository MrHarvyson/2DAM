
# JAVAFX

Como ya hemos visto, la aplicación javafx más simple está formada por un archivo main que será el que inicie la aplicación y cargue la primera ventana, un archivo fxml (diseño visual de la pantalla) y su controlador. Por cada pantalla nueva que creemos tendremos un FXML y un CONTROLLER.

## Análisis del Main
Este archivo iniciará nuestra aplicación y será encargada de cargar nuestra primera ventana con el FXMLLoader.

> NOTA: Nosotros siempre llamamos al archivo fxml (dependiendo de la ventana que queramos abrir) y el propio archivo fxml será encargado de buscar su controlador (se verá más adelante).

```java

public class HelloApplication extends Application {
    @Override
    public void start(Stage stage) throws IOException {

        // es una clase en JavaFX que carga un objeto jerárquico a partir de un documento XML (FXML).
        // obtiene la ubicación del archivo FXML
        FXMLLoader fxmlLoader = new FXMLLoader(HelloApplication.class.getResource("hello-view.fxml"));

        // qué elementos de la interfaz de usuario deben aparecer en la ventana y cómo deben organizarse.
        // tambien podemos especificar el tamaño de la ventana aunque podemos suprimirlo y especificarlo
        // en el fxml
        Scene scene = new Scene(fxmlLoader.load(), 320, 240);

        // stage crea una nueva ventana (nos viene desde el argumento)
        stage.setTitle("Hello!");
        // le decimos a la ventana que escena debe cargar
        stage.setScene(scene);

        // esencial el metodo show para que nos salga en pantalla la ventana
        stage.show();
    }


    public static void main(String[] args) {
        launch();
    }
}

```

## Análisis del FXML

```xml
<?xml version="1.0" encoding="UTF-8"?>

<?import javafx.geometry.*?>
<?import javafx.scene.control.*?>
<?import javafx.scene.layout.*?>

<VBox alignment="CENTER" prefHeight="148.0" prefWidth="184.0" spacing="20.0" xmlns="http://javafx.com/javafx/11.0.14-internal" xmlns:fx="http://javafx.com/fxml/1" fx:controller="com.example.inicio_javafx.HelloController">
    <padding>
        <Insets bottom="20.0" left="20.0" right="20.0" top="20.0" />
    </padding>

   <Label text="Nombre base de datos:" />


   <TextField fx:id="idNombre" />

   <Label text="Contraseña:" />

   <PasswordField fx:id="idContrasena" />

    <Button minWidth="300.0" onAction="#entrar" text="ENTRAR" />

   <Label fx:id="respuesta" />
</VBox>


```

En la etiqueta de VBox encontraremos el vinculo entre el FXML y el controlador `<VBox ... fx:controller="com.example.inicio_javafx.HelloController">`

> IMPORTANTE: Si se cambia el nombre del controlador hay asegurarse que esta el `fx:controller` correcto.












