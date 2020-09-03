---
title: Visual C++ fragmenty kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 213f4299ac71c08118563a008abe065f2c02423e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655395"
---
# <a name="visual-c-code-snippets"></a>Fragmenty kódu v jazyce Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete použít fragmenty kódu k přidání běžně používaného kódu do souborů kódu jazyka C++. Obecně lze použít fragmenty kódu podobným způsobem jako v jazyce C#, ale sada výchozích fragmentů kódu je odlišná.

 Můžete buď přidat fragment kódu do konkrétního umístění v kódu (vložení), nebo obklopit nějaký vybraný kód pomocí fragmentu kódu.

## <a name="inserting-a-code-snippet"></a>Vložení fragmentu kódu
 Chcete-li vložit fragment kódu, otevřete soubor kódu C++ (. cpp nebo. h), klikněte někam do souboru a proveďte jednu z následujících akcí:

- Kliknutím pravým tlačítkem získáte kontextovou nabídku a vyberete **Vložit fragment** .

- V nabídce **Upravit/IntelliSense** vyberte **Vložit fragment** .

- Používat klávesové zkratky: **CTRL + K + X**

  Měl by se zobrazit seznam voleb počínaje **#if**. Když vyberete **#if**, měl by se zobrazit následující kód přidaný do souboru:

```cpp
#if 0

#endif // 0
```

 Hodnotu 0 pak můžete nahradit správnou podmínkou.

## <a name="using-a-code-snippet-to-surround-selected-code"></a>Použití fragmentu kódu k obklopení vybraného kódu
 Chcete-li použít fragment kódu k obklopení vybraného kódu, vyberte řádek (nebo několik řádků) a proveďte jednu z následujících akcí:

1. Kliknutím pravým tlačítkem myši získáte kontextovou nabídku a vyberete možnost **uzavřít s**

2. V nabídce **Upravit/IntelliSense** vyberte **uzavřít s**

3. Použijte klávesové zkratky **CTRL + K + S** .

   Vyberte **#if**. Měli byste vidět přibližně toto:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

 Hodnotu 0 pak můžete nahradit správnou podmínkou.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Kde najdu úplný seznam fragmentů kódu jazyka C++?
 Úplný seznam fragmentů kódu jazyka C++ můžete najít tak, že ve **Správci fragmentů kódů** (v nabídce **nástroje** ) nastavíte **jazyk** na **Visual C++**. V okně níže rozbalte **Visual C++**. Měli byste vidět názvy všech fragmentů kódu C++ v abecedním pořadí.

 Názvy většiny fragmentů kódu jsou samozřejmé, ale některé názvy můžou být matoucí.

## <a name="class-vs-classi"></a>Třída vs. třídy
 Fragment **třídy** poskytuje definici třídy s názvem MyClass, s příslušným výchozím konstruktorem a destruktorem, kde definice konstruktoru a destruktoru jsou umístěné vně třídy:

```cpp
class MyClass
{
public:
MyClass();
~MyClass();

private:

};

MyClass::MyClass()
{
}

MyClass::~MyClass()
{
}
```

 Fragment kódu třídy také poskytuje definici třídy s názvem MyClass, ale výchozí konstruktor a destruktor jsou definovány uvnitř definice třídy:

```cpp
class MyClass
{
public:
MyClass()
{
}

~MyClass()
{
}

private:

};
```

## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>Pro vs. ForEach vs. forr vs rfor
 Existují čtyři různé pro fragmenty kódu, které poskytují různé druhy smyčky for.

 **Pro** fragment kódu poskytuje `for` smyčku, ve které je podmínka založena na délce (v `size_t` ) objektu:

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

 Fragment příkazu **foreach** poskytuje `for each` smyčku, která prochází členy kolekce:

```cpp
for each (object var in collection_to_loop)
{

}
```

 Fragment **forr** poskytuje reverzní `for` smyčku, ve které je podmínka založena na délce (v celých číslech) objektu:

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

 Fragment **rfor** poskytuje smyčku for (odkaz) [na základě rozsahu](https://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) :

```cpp
for (auto& i : v)
{

}
```

## <a name="the-destructor-snippet-"></a>Fragment destruktoru (~)
 Fragment kódu destruktoru ( **~** ) zobrazuje různé chování v různých kontextech. Pokud vložíte tento fragment kódu dovnitř třídy, poskytne destruktor pro tuto třídu. Například s ohledem na následující kód:

```cpp
class SomeClass {

};
```

 Pokud vložíte fragment kódu destruktoru, poskytuje destruktor pro SomeClass:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

 Pokud se pokusíte vložit fragment destruktoru mimo třídu, poskytuje destruktor se zástupným názvem:

```cpp
~TypeNamePlaceholder()
{

```
