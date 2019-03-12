# CSharp File IO 

@ Namespace:System.IO 

@ MSDN : https://docs.microsoft.com/en-us/dotnet/api/system.io.file?view=netframework-4.7.2


FileStream Class
------------------------------------

- FileStream(String, FileMode, FileAccess) 
        Initializes a new instance of the FileStream class with the specified path, creation mode, and read/write permission.
        
StreamWriter Class 
------------------------------------

- StreamWriter(Stream) 
        Initializes a new instance of the StreamWriter class for the specified stream by using UTF-8 encoding and the default buffer size.
        
StreamReader Class 
------------------------------------

-StreamReader(Stream) 
        Initializes a new instance of the StreamReader class for the specified stream.

        ex)
        string path = @"c:\temp\MyTest.txt";
        FileStream fs = new FileStream(path, FileMode.Append, FileAccess.Write);
        
        // stream writer
        StreamWriter writer = new StreamWriter(fs);
        writer.WriteLine("Julia");
        
        // stream reader
        using (StreamReader sr = new StreamReader(fs(path, FileMode.Open)))
        {
                while (sr.Peek() >= 0)
                {
                    Console.WriteLine(sr.ReadLine());
                }
        }
