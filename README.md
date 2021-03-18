# Manipulando pastas com File

### File - Representação abstrata de um arquivo e seu caminho
* https://docs.oracle.com/javase/10/docs/api/java/io/File.html

### Scanner - Leitor de texto
* https://docs.oracle.com/javase/10/docs/api/java/util/Scanner.html



```java
import java.io.File;
import java.util.Scanner;

public class Program {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.println("Enter a folder path: ");
        String strPath = sc.nextLine();

        File path = new File(strPath);

        /* Listar diretórios contidos em um caminho
           Exemplo: c:\windows */
        File[] folders = path.listFiles(File::isDirectory);
        System.out.println("FOLDERS:");
        for (File folder : folders) {
            System.out.println(folder);
        }

        /* Listar arquivos contidos em um caminho
           Exemplo: c:\windows */
        File[] files = path.listFiles(File::isFile);
        System.out.println("FILES:");
        for (File file : files) {
            System.out.println(file);
        }

        // Criar um subdiretório a partir do caminho indicado
        boolean success = new File(strPath + "\\subdir").mkdir();
        System.out.println("Directory created successfully: " + success);

        sc.close();
    }
}
```