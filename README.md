# CSharp File IO 

@ Namespace:System.IO 

@ MSDN : https://docs.microsoft.com/en-us/dotnet/api/system.io.file?view=netframework-4.7.2

Sequential Access 
--------------

- FileStream: read/write bytes
- StreamReader/StreamWriter: Read/Write Characters
- BinaryReader/BinaryWriter: Read/Write Binary Data


FileStream Class
------------------------------------

- FileStream(String, FileMode, FileAccess) 
        Initializes a new instance of the FileStream class with the specified path, creation mode, and read/write permission
        
- FileMode: Append, Create, CreateNew, Open, OpenOrCreate, Truncate

- FileAccess: Read, Write, ReadWrite

        
StreamWriter Class 
------------------------------------

- StreamWriter(Stream) 
        Initializes a new instance of the StreamWriter class for the specified stream by using UTF-8 encoding and the default buffer size.
        
- Write (<all intrinsic types>), WriteLine (<all intrinsic types>), Flush, Close
        
StreamReader Class 
------------------------------------

-StreamReader(Stream) 
        Initializes a new instance of the StreamReader class for the specified stream.
  
- Read(), Read(char[]), ReadLine, ReadToEnd

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

BinaryWriter & BinaryReader Class 
--------------------

- binary files store the binary image of actual data values instead of storing data as a sequence of characters

*  a 32 bit integer occupies four bytes 

*  used to work with fixed length records to facilitate easy position based access

wr.Write (name.PadRight(LENGTH).ToCharArray(0, LENGTH)); 

string name = new String(binaryReader.ReadChars(50));




        ex) 
        string fileName = "AppSettings.dat";

        using (BinaryWriter writer = new BinaryWriter(File.Open(fileName, FileMode.Create)))
        {
                writer.Write(1.250F);
                writer.Write(@"c:\Temp");
                writer.Write(10);
                writer.Write(true);
        }

        using (BinaryReader reader = new BinaryReader(File.Open(fileName, FileMode.Open)))
        {
                aspectRatio = reader.ReadSingle();
                tempDirectory = reader.ReadString();
                autoSaveTime = reader.ReadInt32();
                showStatusBar = reader.ReadBoolean();
        }
