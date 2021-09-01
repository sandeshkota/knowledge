### What is .Net ?


# What is .Net Framework ? .Net Core Framework ? .Net Standard ?


### What is CLR ?
Common Language Runtime
CLR provides additional services including Base Class Library Support, thread management, memory management, type safety, exception handling, garbage collection, and security

### What is CLS ?
Common Language Specification (CLS) under CLR is a set of rules by which languages must flow in order to make them compatible with other .NET languages.  
Ex: No Multiple Inheritance in .net framework

### What is CTS ?
Common Type System - Data types of class members that are created in two different languages get compiled into the base common data type system.  
C# has int Data Type and VB.Net has Integer Data Type - after compilation, use the same structure Int32 from CTS.

### What is GC ?
Garbage Collector automatically releases memory of unused objects in an application and can be done 
by CLR automatically or forcefully by writing a code in an application about how memory management happens in CLR

### Phases in Garbage Collection ?
- Marking Phase: A list of all the live objects is created during the marking phase.
- Relocating Phase: The references of all the objects that were on the list of all the live objects are updated in the relocating phase so that they point to the new location .
- Compacting Phase: The heap gets compacted in the compacting phase as the space occupied by the dead objects is released and the live objects remaining are moved.

### Generations in GC ?
- Gen 1: short lived objects
- Gen 2: if gen 1 objects are not deleted after GC run, it is moved to Gen 2
- Gen 3: if gen 2 objects are not deleted after GC run, it is moved to Gen 3 . Ex: Static Objects
```csharp
// to get object generation
GC.GetGeneration(obj)

// Force GC Collection by passing the generation number
GC.Collect(0)
```

### JIT ?
In short, our code gets compiled two times. On the first pass, it is compiled from higher language to MSIL (Microsoft Intermediate Language). 
During the second pass, the code (now an assembly in MSIL) is compiled into machine language which is understandable by the operating system.

C# Code > C# Compiler (csc.exe) > IL > .NET Runtime > JIT Compiler > Machinecode > Execution
VB Code > VB Compiler           > IL > .NET Runtime > JIT Compiler > Machinecode > Execution



