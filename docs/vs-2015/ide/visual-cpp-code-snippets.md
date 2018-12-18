---
title: Fragmenty kódu Visual C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e26fd4-e5ca-4611-a816-0a521b4947a0
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ed64d9dde53b31cfe5f52ce708e4ee96d91fe8ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861357"
---
# <a name="visual-c-code-snippets"></a>Fragmenty kódu v jazyce Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kódu v sadě Visual Studio slouží k přidání běžně používá kód pro soubory kódu C++. Obecně platí fragmenty kódu můžete použít stejným způsobem jako v jazyce C#, ale sada výchozí fragmenty kódu se liší.  
  
 Můžete přidat fragment kódu do určitého umístění ve vašem kódu (vložení) nebo před a za některých vybraný kód fragmentem kódu.  
  
## <a name="inserting-a-code-snippet"></a>Vložení fragmentu kódu  
 Vložit fragment kódu, otevřete soubor kódu jazyka C++ (.cpp a .h), klikněte někam do souboru a proveďte jednu z následujících akcí:  
  
- Klikněte pravým tlačítkem a získat kontextovou nabídku a vyberte **Vložit fragment**  
  
- V **upravit / IntelliSense** příkaz **Vložit fragment**  
  
- Použití klávesových zkratek: **CTRL + K, X**  
  
  Zobrazí se seznam možností počínaje **#if**. Když vyberete **#if**, byste měli vidět následující kód do souboru přidán:  
  
```cpp  
#if 0  
  
#endif // 0  
```  
  
 0 můžete nahradit pak správná podmínku.  
  
## <a name="using-a-code-snippet-to-surround-selected-code"></a>Fragment kódu pomocí ohraničit vybraný kód  
 Použití kódu před a za vybraný kód, vyberte řádek (nebo více řádků) a proveďte jednu z následujících akcí:  
  
1. Klikněte pravým tlačítkem a získat kontextovou nabídku a vyberte **obklopit fragmentem**  
  
2. V **upravit / IntelliSense** příkaz **obklopit fragmentem**  
  
3. Použití klávesových zkratek: **K, CTRL + S**  
  
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
 **Třídy** fragment kódu obsahuje definice třídy s názvem MyClass, s odpovídající výchozí konstruktor a destruktor, kde se nachází definice konstruktor a destruktor mimo třídu:  
  
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
  
 Fragment kódu classi také obsahuje definici třídy s názvem MyClass, ale jsou definovány výchozí konstruktor a destruktor uvnitř definice třídy:  
  
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
  
## <a name="for-vs-foreach-vs-forr-vs-rfor"></a>Pro porovnání foreach vs. rfor díky vs  
 Existují čtyři různé pro fragmenty kódu, které poskytují různé typy ze smyčky for.  
  
 **Pro** poskytuje fragment kódu `for` smyčku, ve kterém podmínka je na základě délky (v `size_t`) objektu:  
  
```cpp  
for (size_t i = 0; i < length; i++)  
{  
  
}  
```  
  
 **Foreach** poskytuje fragment kódu `for each` smyčku, která iteruje přes členů kolekce:  
  
```cpp  
for each (object var in collection_to_loop)  
{  
  
}  
```  
  
 **Díky** fragment kódu obsahuje obrácenou `for` smyčku, ve kterém podmínka je na základě délky (v celých čísel) objektu:  
  
```cpp  
for (int i = length - 1; i >= 0; i--)  
{  
  
}  
```  
  
 **Rfor** poskytuje fragment kódu [založený na rozsahu](http://msdn.microsoft.com/library/5750ba1d-ba48-4236-a923-e32de8345c2d) pro smyčky (odkaz):  
  
```cpp  
for (auto& i : v)  
{  
  
}  
```  
  
## <a name="the-destructor-snippet-"></a>Fragment kódu – destruktor (~)  
 Fragment kódu – destruktor (**~**) ukazuje různé chování v různých kontextech. Pokud je vložit tento fragment kódu uvnitř třídy, obsahuje destruktor pro danou třídu. Mějme například následující kód:  
  
```cpp  
class SomeClass {  
  
};  
```  
  
 Při vložení fragmentu kódu destruktor obsahuje destruktor pro SomeClass:  
  
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



