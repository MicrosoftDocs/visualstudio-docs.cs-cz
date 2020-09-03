---
title: 'Postupy: Změna výstupního adresáře sestavení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b665f5788d12c294e8ab7f55ecc63d183030a0ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645435"
---
# <a name="how-to-change-the-build-output-directory"></a>Postupy: Změna výstupního adresáře sestavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete určit umístění výstupu podle konfigurace (pro ladění, vydání nebo obojí) generované vaším projektem.

> [!NOTE]
> Pokud máte projekt **instalace** , podívejte se na poznámku na konci tohoto článku.

## <a name="changing-the-build-output-directory"></a>Změna výstupního adresáře sestavení

#### <a name="to-change-the-build-output-directory"></a>Změna výstupního adresáře sestavení

1. V panelu nabídek vyberte položku projekt, **vlastnosti** **aplikace** *AppName* . Můžete také kliknout pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vybrat **vlastnosti**.

2. Pokud máte projekt Visual Basic, vyberte kartu **kompilovat** . Máte-li projekt jazyka Visual C#, vyberte kartu **sestavení** . Pokud máte projekt C++ nebo JavaScriptový projekt, vyberte kartu **Obecné** .

3. V rozevíracím seznamu konfigurace v horní části vyberte konfiguraci, jejíž umístění výstupního souboru chcete změnit (ladit, vydaná verze nebo všechny).

     Najde výstupní cestu k cestě (**výstupní cesta sestavení** v Visual Basic, **výstupní adresář** v Visual C++, **výstupní cestu** v jazyce JavaScript a C#). Zadejte nový výstupní adresář sestavení relativní vzhledem k adresáři projektu.

> [!NOTE]
> V projektu instalace se v poli **název výstupního souboru** mění pouze umístění souboru Setup.exe, nikoli umístění souborů projektu. Další informace naleznete v tématu **sestavení, vlastnosti konfigurace, dialogové okno Vlastnosti projektu nasazení**.

## <a name="see-also"></a>Viz také
 [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md) [Obecná stránka vlastností (projekt)](https://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45) [kompilace a sestavování](../ide/compiling-and-building-in-visual-studio.md)
