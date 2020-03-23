---
title: Výstřižky kódu Visual C++
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: db6ea1e233d32872322926a4d75b847ee6a49ba3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77277830"
---
# <a name="visual-c-code-snippets"></a>Výstřižky kódu Visual C++

V sadě Visual Studio můžete pomocí fragmentů kódu přidat běžně používaný kód do souborů kódu jazyka C++. Obecně lze použít fragmenty kódu v podstatě stejným způsobem jako v jazyce C#, ale sada výchozích fragmentů kódu se liší.

Můžete buď přidat fragment kódu na určité místo v kódu (vložení) nebo obklopit nějaký vybraný kód fragmentem kódu.

## <a name="insert-a-code-snippet"></a>Vložení fragmentu kódu

Chcete-li vložit fragment kódu, otevřete soubor kódu Jazyka C++ (*CPP* nebo *.h*), klepněte někde uvnitř souboru a proveďte jednu z následujících akcí:

- Kliknutím pravým tlačítkem myši získáte místní nabídku a vyberte **Vložit úryvek.**

- V nabídce **Upravit / IntelliSense** vyberte **Vložit úryvek.**

- Použití klávesových zkratek: **Ctrl**+**K**+**X**

Měli byste vidět seznam voleb **začínajících #if**. Když vyberete **#if**, měli byste vidět následující kód přidaný do souboru:

```cpp
#if 0

#endif // 0
```

Potom můžete nahradit **0** se správnou podmínkou.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Použití fragmentu kódu k obsazu vybraného kódu

Chcete-li použít fragment kódu k obsuzu, vyberte řádek (nebo více řádků) a proveďte jednu z následujících akcí:

- Kliknutím pravým tlačítkem myši získáte kontextovou nabídku a vyberte **možnost Obklopit se**

- V nabídce **Upravit** > **technologie IntelliSense** vyberte **Možnost Obklopit pomocí**

- Pomocí klávesnice stiskněte: **Ctrl**+**K**+**S**

Vyberte **#if**. Mělo by se vám zobrazit přibližně toto:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

Potom můžete nahradit 0 se správnou podmínkou.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Kde najdu úplný seznam fragmentů kódu Jazyka C++?

Úplný seznam fragmentů kódu jazyka C++ najdete tak, že přejdete do **Správce výstřižků kódu** (v nabídce **Nástroje)** a nastavíte **jazyk** na **Visual C++**. V okně níže rozbalte **Visual C++**. Měli byste vidět názvy všech fragmentů kódu Jazyka C++ v abecedním pořadí.

Názvy většiny fragmentů kódu jsou samozřejmé, ale některé názvy mohou být matoucí.

## <a name="class-vs-classi"></a>Třída vs. classi

Fragment **třídy** poskytuje definici třídy `MyClass`s názvem , s příslušným výchozím konstruktorem a destruktorem, kde jsou definice konstruktoru a destruktoru umístěny mimo třídu:

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

Fragment kódu **classi** také poskytuje definici třídy `MyClass`s názvem , ale výchozí konstruktor a destruktor jsou definovány uvnitř definice třídy:

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

## <a name="for-vs-forr-vs-rfor"></a>pro vs. forr vs rfor

Existují tři různé **pro** úryvky, `for` které poskytují různé druhy smyček.

Úryvek **rfor** poskytuje smyčku (link) [založenou na rozsahu.](/cpp/cpp/range-based-for-statement-cpp) Tato konstrukce je upřednostňována před smyčkami založenými na `for` indexu.

```cpp
for (auto& i : v)
{

}
```

**For** úryvek poskytuje `for` smyčku, ve které je `size_t`podmínka založena na délce (v ) objektu.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**Forr** fragment poskytuje reverzní `for` smyčky, ve kterém je podmínka založena na délce (v celá čísla) objektu.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Fragment destruktoru (~)

Fragment destruktoru (**~**) zobrazuje různé chování v různých kontextech. Pokud vložíte tento úryvek uvnitř třídy, poskytuje destruktor pro tuto třídu. Například s následujícím kódem:

```cpp
class SomeClass {

};
```

Pokud vložíte fragment destruktoru, poskytne destruktor `SomeClass`pro :

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Pokud se pokusíte vložit fragment destruktoru mimo třídu, poskytne destruktor se zástupným názvem:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)