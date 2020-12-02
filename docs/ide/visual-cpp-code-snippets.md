---
title: Visual C++ fragmentů kódu
description: Naučte se používat fragmenty kódu k přidání běžně používaného kódu do souborů kódu jazyka C++.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: corob-msft
ms.author: corob
manager: markl
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: e5cde2be817c49344e02ff06030022f99790a7a2
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478806"
---
# <a name="visual-c-code-snippets"></a>Visual C++ fragmentů kódu

V aplikaci Visual Studio můžete použít fragmenty kódu k přidání běžně používaného kódu do souborů kódu jazyka C++. Obecně lze použít fragmenty kódu podobným způsobem jako v jazyce C#, ale sada výchozích fragmentů kódu je odlišná.

Můžete buď přidat fragment kódu do konkrétního umístění v kódu (vložení), nebo obklopit nějaký vybraný kód pomocí fragmentu kódu.

## <a name="insert-a-code-snippet"></a>Vložení fragmentu kódu

Chcete-li vložit fragment kódu, otevřete soubor kódu C++ (*. cpp* nebo *. h*), klikněte někam do souboru a proveďte jednu z následujících akcí:

- Kliknutím pravým tlačítkem získáte kontextovou nabídku a vyberete **Vložit fragment** .

- V nabídce **Upravit/IntelliSense** vyberte **Vložit fragment** .

- Používat klávesové zkratky: **CTRL +** + **K** + **X**

Měl by se zobrazit seznam voleb počínaje **#if**. Když vyberete **#if**, měl by se zobrazit následující kód přidaný do souboru:

```cpp
#if 0

#endif // 0
```

**Hodnotu 0** pak můžete nahradit správnou podmínkou.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Použití fragmentu kódu k obklopení vybraného kódu

Chcete-li použít fragment kódu k obklopení vybraného kódu, vyberte řádek (nebo několik řádků) a proveďte jednu z následujících akcí:

- Kliknutím pravým tlačítkem myši získáte kontextovou nabídku a vyberete možnost **uzavřít s**

- V nabídce **Upravit**  >  **IntelliSense** vyberte **uzavřít s**

- Pomocí klávesnice stiskněte klávesu **CTRL** + **K** + **S** .

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

Fragment **třídy** poskytuje definici třídy s názvem `MyClass` s příslušným výchozím konstruktorem a destruktorem, kde definice konstruktoru a destruktoru jsou umístěné vně třídy:

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

Fragment kódu **třídy** také poskytuje definici třídy s názvem `MyClass` , ale výchozí konstruktor a destruktor jsou definovány uvnitř definice třídy:

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

Existují tři různé **pro** fragmenty kódu, které poskytují různé druhy `for` smyček.

Fragment kódu **rfor** poskytuje smyčku for (odkaz) [na základě rozsahu](/cpp/cpp/range-based-for-statement-cpp) . Tento konstruktor je upřednostňován přes smyčky založené na indexu `for` .

```cpp
for (auto& i : v)
{

}
```

**Pro** fragment kódu poskytuje `for` smyčku, ve které je podmínka založena na délce (v `size_t` ) objektu.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

Fragment **forr** poskytuje reverzní `for` smyčku, ve které je podmínka založena na délce (v celých číslech) objektu.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Fragment destruktoru (~)

Fragment kódu destruktoru ( **~** ) zobrazuje různé chování v různých kontextech. Pokud vložíte tento fragment kódu dovnitř třídy, poskytne destruktor pro tuto třídu. Například s ohledem na následující kód:

```cpp
class SomeClass {

};
```

Pokud vložíte fragment kódu destruktoru, poskytuje destruktor pro `SomeClass` :

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

## <a name="see-also"></a>Viz také

- [Fragmenty kódu](../ide/code-snippets.md)