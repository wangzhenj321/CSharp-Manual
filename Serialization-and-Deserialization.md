## Introduction

In simple words, we can say an object conversion in text stream is serialization and text stream conversion in object of a class is called deserialization. Or we can say XML serialization is the process of converting an object's **public** properties and fields to a serial format (in this case, XML) for storage or transport. Deserialization re-creates the object in its original state from the XML output.

Let's say I have a complex object which has a hierarchy of classes. Now in case we need XML stream from this object, we will go for serialization. In the same manner, we have XML **string** and we want to convert this in a class and object format, we will go for deserialization.

## Why Serialization and Deserialization

Let's say we have a very complex object and we need XML format for our XSLT rendering on HTML page. Then we have one option that we will write a XML file in the disk after parsing object variable and than load the XML file in **XmlDocument** object. But is it really a good approach? No, of course not. Why so. This is because in large applications, we have so many users and we will be writing files for every one. This will take lots of space as well as it is risky that might be files are shared among the users or any human being can read that file. 
So what do we do now? Yes at this time, go with serialization, get an XML **string** and just load it to **XmlDocument**. This will be done in code.

This can be implemented with web services. When we have created a proxy of any web service and we need to send and receive response, it is very beneficial.

## How Do We Achieve This

First note that for serialization and deserialization, we need to use **System.Xml.Serialization**, because we need to use **XmlSerialization** class which is provided in **System.Xml.Serialization**.

To understand this, we assume one example of Category and Items. We have two classes. One is Category and another is Items. Category has CategoryID, Category Name and Array of Item. While Item has Item ID, Item Name, Item Price and Item Quantity in Stock.

```C#
public class Category
{
    private int _CatID;
    private string _CatName;
    private Item[] _Item;

    public int CateboryID
    {
        get
        {
            return _CatID;
        }
        set
        {
            _CatID = value;
        }
    }

    public string CategoryName
    {
        get
        {
            return _CatName;
        }
        set
        {
            _CatName = value;
        }
    }


    public Item[] Item
    {
        get
        {
            return _Item;
        }
        set
        {
            _Item = value;
        }
    }
}
```

```C#
public class Item
{
    private int _ItemID;
    private string _ItemName;
    private int _ItemPrice;
    private int _ItemQtyInStock;

    public int ItemID
    {
        get
        {
            return _ItemID;
        }
        set
        {
            _ItemID = value;
        }
    }

    public string ItemName
    {
        get
        {
            return _ItemName;
        }
        set
        {
            _ItemName = value;
        }
    }

    public int ItemPrice
    {
        get
        {
            return _ItemPrice;
        }
        set
        {
            _ItemPrice = value;
        }
    }

    public int ItemQtyInStock
    {
        get
        {
            return _ItemQtyInStock;
        }
        set
        {
            _ItemQtyInStock = value;
        }
    }
}
```

## Let’s First Understand Serialization

In our application, we have serialization function which is called by our click event or whenever this is required. In serialization, we have created one object of Category class and another is Item. Category holds one test category “Phone” and then it creates an array of Item class and stores to Category.Item.

```C#
private void Serialization()
    {
        Category Cat = new Category();
        Cat.CateboryID = 1;
        Cat.CategoryName = "Phone";
        Item[] Itm = new Item[5];
        for (int i = 0; i &lt; 5; i++)
        {
            Itm[i] = new Item();
            Itm[i].ItemID = i;
            Itm[i].ItemPrice = i * 10;
            Itm[i].ItemQtyInStock = i + 10;
            Itm[i].ItemName = " Item Name : " + i.ToString();

        }
        Cat.Item = Itm;
        XmlSerializer ser = new XmlSerializer(Cat.GetType());
        System.Text.StringBuilder sb = new System.Text.StringBuilder();
        System.IO.StringWriter writer = new System.IO.StringWriter(sb);
        ser.Serialize(writer, Cat); 	// Here Classes are converted to XML String. 
				// This can be viewed in SB or writer.
        // Above XML in SB can be loaded in XmlDocument object
        XmlDocument doc = new XmlDocument();
        doc.LoadXml(sb.ToString());
    }
```

Here Ser is the object of **System.Xml.Serialization.XmlSerializer** class. It gets the Type of Category class object by Cat.GetType(). ser.Serialize takes two parameters, one is string writer like a target object and another is Cat that is source object. This converts or Serializes Cat object and stores stream into a writer object. Now object is converted into XML string and we can find that by using stringbuilder’s object. Like sb.ToString(). This string can be loaded in XML document for further traversing.

## Let’s have look at Deserialization

In our application, we have Deserialization function which is called by our click event or whenever this is required. In deserialization, we have created one object of Category class.

```C#
protected void DeSerialize(string XmlString)
    {
        Category Cat = new Category();
        XmlDocument doc = new XmlDocument();
        doc.LoadXml (XmlString);
        XmlNodeReader reader = new XmlNodeReader(doc.DocumentElement);
        XmlSerializer ser = new XmlSerializer(Cat.GetType());
        object obj = ser.Deserialize(reader);
        // Then you just need to cast obj into whatever type it is, e.g.:
        Category myObj = (Category)obj;
        Now Ser
    }
```

#### XMLString for DeSerialization

```XML
<?xml version="1.0" encoding="utf-16"?>
<Category>
      <CateboryID>1</CateboryID>
      <CategoryName>Phone</CategoryName>
      <Item>
            <Item>
                  <ItemID>0</ItemID>
                  <ItemName> Item Name : 0</ItemName>
                  <ItemPrice>0</ItemPrice>
                  <ItemQtyInStock>10</ItemQtyInStock>
            </Item>
            <Item>
                  <ItemID>1</ItemID>
                  <ItemName> Item Name : 1</ItemName>
                  <ItemPrice>10</ItemPrice>
                  <ItemQtyInStock>11</ItemQtyInStock>
            </Item>
            <Item>
                  <ItemID>2</ItemID>
                  <ItemName> Item Name : 2</ItemName>
                  <ItemPrice>20</ItemPrice>
                  <ItemQtyInStock>12</ItemQtyInStock>
            </Item>
            <Item>
                  <ItemID>3</ItemID>
                  <ItemName> Item Name : 3</ItemName>
                  <ItemPrice>30</ItemPrice>
                  <ItemQtyInStock>13</ItemQtyInStock>
            </Item>
            <Item>
                  <ItemID>4</ItemID>
                  <ItemName> Item Name : 4</ItemName>
                  <ItemPrice>40</ItemPrice>
                  <ItemQtyInStock>14</ItemQtyInStock>
            </Item>
      </Item>
</Category>
```

In the above code, we are passing one XML string. This will be converted into a form of object. Here XML string is loaded into XmlDocument object and then XmlNodeReader is reading from it. Now XmlSerialize object is created and we let it know the type of object by Cat.GetType(). Now Ser object knows that it has to convert XML into an object of Category Type. Now ser.Deserialize(reader) takes XML from reader object and converts into an Object. Later this object is cast into category. If we add this object into watch and view, we will find that it has created the class hierarchy.

## Usage of XmlDocument.LoadXml

```C#
using System;
using System.Xml;

public class Sample
{
    public static void Main()
    {
        // Create the XmlDocument.
        XmlDocument doc = new XmlDocument();
        doc.LoadXml("<item><name>wrench</name></item>");

        // Add a price element.
        XmlElement newElem = doc.CreateElement("price");
        newElem.InnerText = "10.95";
        doc.DocumentElement.AppendChild(newElem);

        XmlWriterSettings settings = new XmlWriterSettings();
        settings.Indent = true;
        // Save the document to a file and auto-indent the output.
        XmlWriter writer = XmlWriter.Create("data.xml", settings);
        doc.Save(writer);
    }
}

/*
<?xml version="1.0" encoding="utf-8"?>
<item>
  <name>wrench</name>
  <price>10.95</price>
</item>
*/
```

## References
1. [Serialization and Deserialization in ASP.NET with C#](https://www.codeproject.com/Articles/36781/Serialization-and-Deserialization-in-ASP-NET-with)