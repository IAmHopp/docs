---
title: "Instance Constructors - C# Programming Guide"
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords: 
  - "constructors [C#], instance constructors"
  - "instance constructors [C#]"
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
---
# Instance Constructors (C# Programming Guide)

Instance constructors are used to create and initialize any instance member variables when you use the [new](../../../csharp/language-reference/operators/new-operator.md) expression to create an object of a [class](../../../csharp/language-reference/keywords/class.md). To initialize a [static](../../../csharp/language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor. For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 The following example shows an instance constructor:  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
>  For clarity, this class contains public fields. The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings. Data members should generally be private, and should be accessed only through class methods and properties.  
  
 This instance constructor is called whenever an object based on the `Coords` class is created. A constructor like this one, which takes no arguments, is called a *parameterless constructor*. However, it is often useful to provide additional constructors. For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 This allows `Coords` objects to be created with default or specific initial values, like this:  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields. For example, an [int](../../../csharp/language-reference/keywords/int.md) is initialized to 0. For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md). Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works. A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.  
  
 Instance constructors can also be used to call the instance constructors of base classes. The class constructor can invoke the constructor of the base class through the initializer, as follows:  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived. A complete example using `Shape` and `Circle` appears in this topic as Example 3.  
  
## Example 1  
 The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## Example 2  
 In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 Notice that the default value of `age` is `0` and the default value of `name` is `null`. For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## Example 3  
 The following example demonstrates using the base class initializer. The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class. The constructor on each derived class is using its base class initializer.  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 For more examples on invoking the base class constructors, see [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md), and [base](../../../csharp/language-reference/keywords/base.md).  
  
## See also

- [C# Programming Guide](../../../csharp/programming-guide/index.md)
- [Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [static](../../../csharp/language-reference/keywords/static.md)
