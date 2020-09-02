---
title: Operátor kontextu v ladicím programu (C++) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.operators
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C++], native debugger
- evaluation
- format specifiers, expressions
- context operator, in expressions
- debugging [C++], expressions
- native expression evaluator
ms.assetid: 73cc9afe-f4a4-474e-bb89-5a33fb5e570c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: aa16bd6f93198e5360139dbc5a6a0d96f02a1e41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62564701"
---
# <a name="context-operator-in-the-visual-studio-debugger-c"></a>Operátor kontextu v ladicím programu sady Visual Studio (C++)
Operátor kontextu v jazyce C++ lze použít k získání umístění zarážky, názvu proměnné nebo výrazu. Kontextový operátor je vhodný pro zadání názvu z vnějšího oboru, který je jinak skrytý místními názvy.

## <a name="syntax"></a><a name="BKMK_Using_context_operators_to_specify_a_symbol"></a> Syntaktick
 Existují dva způsoby určení kontextu:

1. {,, [*modul*]} *výraz*

     Složené závorky musí obsahovat dvě čárky a název modulu (spustitelný soubor nebo knihovna DLL) nebo úplnou cestu.

     Například chcete-li nastavit zarážku na `SomeFunction` funkci EXAMPLE.dll:

    ```C++
    {,,EXAMPLE.dll}SomeFunction
    ```

2. *modul*! *výraz*

    ```C++
    EXAMPLE.dll!SomeFunction
    ```

- *modul* je název modulu. Můžete použít úplnou cestu k jednoznačnému rozlišit moduly se stejným názvem.

   Pokud cesta k *modulu* obsahuje čárku, vloženou mezeru nebo složenou závorku, je nutné použít uvozovky kolem cesty, aby analyzátor kontextu mohl správně rozpoznat řetězec. Jednoduché uvozovky se považují za součást názvu souboru systému Windows, takže je nutné použít dvojité uvozovky. Příklad:

  ```C++
  {,,"a long, long, library name.dll"} g_Var
  ```

- *výraz* je libovolný platný výraz C++, který se překládá na platný cíl, jako je název funkce, název proměnné nebo adresa ukazatele v *modulu*.

  Když vyhodnocovací filtr výrazů nalezne symbol ve výrazu, vyhledá symbol v následujícím pořadí:

1. Lexikální rozsah směrem ven, počínaje aktuálním blokem, řadou příkazů uzavřenými ve složených závorkách a pokračování ven s ohraničujícím blokem. Aktuální blok je kód obsahující aktuální umístění, adresu ukazatele na instrukci.

2. Rozsah funkce Aktuální funkce

3. Obor třídy, pokud je aktuální umístění uvnitř členské funkce jazyka C++. Obor třídy zahrnuje všechny základní třídy. Vyhodnocovací filtr výrazů používá normální pravidla dominantního postavení.

4. Globální symboly v aktuálním modulu.

5. Veřejné symboly v aktuálním programu.