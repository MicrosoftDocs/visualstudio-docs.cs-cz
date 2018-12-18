---
title: Fragmenty kódu Visual C++
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: f119f3b2bc438eacfaaa722bd57fb440aa303052
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948925"
---
# <a name="visual-c-code-snippets"></a>Fragmenty kódu Visual C++

Fragmenty kódu v sadě Visual Studio slouží k přidání běžně používá kód pro soubory kódu C++. Obecně platí fragmenty kódu můžete použít stejným způsobem jako v jazyce C#, ale sada výchozí fragmenty kódu se liší.

Můžete přidat fragment kódu do určitého umístění ve vašem kódu (vložení) nebo před a za některých vybraný kód fragmentem kódu.

## <a name="insert-a-code-snippet"></a>Vložit fragment kódu

Chcete-li vložit fragment kódu, otevřete soubor kódu jazyka C++ (*.cpp* nebo *.h*), klikněte někam do souboru, a proveďte jednu z následujících akcí:

- Klikněte pravým tlačítkem a získat kontextovou nabídku a vyberte **Vložit fragment**

- V **upravit / IntelliSense** příkaz **Vložit fragment**

- Použití klávesových zkratek: **Ctrl**+**K**+**X**

Zobrazí se seznam možností počínaje **#if**. Když vyberete **#if**, byste měli vidět následující kód do souboru přidán:

```cpp
#if 0

#endif // 0
```

Pak můžete nahradit **0** s podmínkou správný.

## <a name="use-a-code-snippet-to-surround-selected-code"></a>Pomocí kódu ohraničit vybraný kód

Použití kódu před a za vybraný kód, vyberte řádek (nebo více řádků) a proveďte jednu z následujících akcí:

- Klikněte pravým tlačítkem na získání kontextovou nabídku a vyberte **obklopit fragmentem**

- Z **upravit** > **IntelliSense** příkaz **obklopit fragmentem**

- Použití klávesnice, stiskněte klávesu: **Ctrl**+**K**+**S**

Vyberte **#if**. By měl vypadat přibližně takto:

```cpp
#if 0
#include "pch.h"  // or whatever line you had selected
#endif // 0
```

0 můžete nahradit pak správná podmínku.

## <a name="where-can-i-find-a-complete-list-of-the-c-code-snippets"></a>Kde najdete úplný seznam fragmenty kódu C++

Úplný seznam fragmenty kódu C++ můžete najít tak, že přejdete **Správce fragmentů kódů** (na **nástroje** nabídky) a nastavení **jazyk** k **Visual C++** . V okně níže, rozbalte **Visual C++**. Měli byste vidět názvy všech fragmenty kódu C++ v abecedním pořadí.

Názvy většina fragmentů kódu není potřeba vysvětlovat, ale některé názvy mohou být matoucí.

## <a name="class-vs-classi"></a>Třída vs. classi

**Třídy** fragment kódu obsahuje definici třídy s názvem `MyClass`s odpovídající výchozí konstruktor a destruktor, kde se nachází definice konstruktor a destruktor mimo třídu:

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

**Classi** fragment kódu také poskytuje definici třídy s názvem `MyClass`, ale jsou definovány výchozí konstruktor a destruktor uvnitř definice třídy:

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

## <a name="for-vs-forr-vs-rfor"></a>pro porovnání rfor díky vs

Existují tři různé **pro** fragmenty kódu, které poskytují různé typy z `for` smyčky.

**Rfor** poskytuje fragment kódu [založený na rozsahu](/cpp/cpp/range-based-for-statement-cpp) pro smyčky (odkaz). Tento konstruktor je upřednostňované nad indexu `for` smyčky.

```cpp
for (auto& i : v)
{

}
```

**Pro** poskytuje fragment kódu `for` smyčku, ve kterém podmínka je na základě délky (v `size_t`) objektu.

```cpp
for (size_t i = 0; i < length; i++)
{

}
```

**Díky** fragment kódu obsahuje obrácenou `for` smyčku, ve kterém podmínka je na základě délky (v celých čísel) objektu.

```cpp
for (int i = length - 1; i >= 0; i--)
{

}
```

## <a name="the-destructor-snippet-"></a>Fragment kódu – destruktor (~)

Fragment kódu – destruktor (**~**) ukazuje různé chování v různých kontextech. Pokud je vložit tento fragment kódu uvnitř třídy, obsahuje destruktor pro danou třídu. Mějme například následující kód:

```cpp
class SomeClass {

};
```

Při vložení fragmentu kódu destruktor obsahuje destruktor `SomeClass`:

```cpp
class SomeClass {
    ~SomeClass()
    {

    }
};
```

Pokud se pokusíte vložit fragment – destruktor mimo třídu, poskytuje destruktor zástupný název:

```cpp
~TypeNamePlaceholder()
{
```

## <a name="see-also"></a>Viz také:

- [Fragmenty kódu](../ide/code-snippets.md)