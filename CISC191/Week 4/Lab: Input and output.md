# Change contents in a text file

## Objective
Understand how to edit contents in a text file

## Task
1. Assignment Code:
```Java
import java.io.*;
import java.util.*;

public class InputOutputLab {

    public static void main(String[] args) {
        if (args.length != 1) {
            System.out.println("Usage: java InputOutputLab <input-file>");
            return;
        }

        String inputFileName = args[0];

        try (BufferedReader br = new BufferedReader(new FileReader(inputFileName))) {
            String line;
            while ((line = br.readLine()) != null) {
                if (line.endsWith("_photo.jpg")) {
                    String modifiedFileName = line.replace("_photo.jpg", "_info.txt");
                    System.out.println(modifiedFileName);
                }
            }
        } catch (IOException e) {
            System.out.println("An error occurred while reading the file: " + e.getMessage());
        }
    }
}
```

## This is my flowchart:
<img width="471" height="1261" alt="Lab_ Input and output drawio" src="https://github.com/user-attachments/assets/0ff42993-1891-4b77-86c1-ac98eb48573f" />

## Challenges encountered while performing the lab:
As much fun as I had with the lab, it took me a good 5 minutes to figure out how to edit the Run Configuration to have it run with the Program Arguments, which is ParkPhotos.txt in this case.  
