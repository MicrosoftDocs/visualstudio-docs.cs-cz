---
title: Co je nového v ladicím programu sady Visual Studio 2015 | Dokumentace Microsoftu
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, what's new
- what's new [debugger]
- debugging [Visual Studio], what's new
- what's new [Visual Studio], debugging
ms.assetid: 2aed9caa-2384-4e49-8595-82d8b06cf271
caps.latest.revision: 86
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 261b3f42cb5c1040567ef16c62d3c44c5d60e0b3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065388"
---
# <a name="whats-new-for-the-debugger-in-visual-studio-2015"></a>Novinky v ladicím programu sady Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Informace o všechno, co je nového ve Visual Studio 2015 Update 1 ladění a Diagnostika, naleznete v tématu [Visual Studio 2015 Update 1 zpráva k vydání verze](https://www.visualstudio.com/news/vs2015-update1-vs#debug).

 Informace o všechno, co je nového ve Visual Studio 2015 RTM ladění a Diagnostika, naleznete v tématu [Visual Studio 2015 – poznámky k](https://www.visualstudio.com/news/vs2015-vs#debug).

## <a name="visual-studio-2015-update-1-changes"></a>Visual Studio 2015 Update 1 změny
 C++ upravit a pokračovat podporuje další funkce. Další informace najdete v tématu [upravit a pokračovat (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).

 Ladění narušení přístupu Visual C++, určuje nové dialogové okno výjimky ukazatel, který způsobil výjimku. Další informace najdete v tématu [jak mohu ladit narušení přístupu?](../debugger/how-can-i-debug-an-access-violation-q.md) a [vylepšení ladění narušení přístupu jazyka C++ ve Visual Studio 2015 Update 1](http://blogs.msdn.com/b/visualstudioalm/archive/2015/10/29/improvement-to-debugging-c-access-violations-in-visual-studio-2015-update-1.aspx)

## <a name="visual-studio-2015-rtm-debugger-ui-and-hotkey-changes"></a>Visual Studio 2015 RTM ladicího programu uživatelského rozhraní a změny klávesová zkratka
 Existují významné změny uživatelského rozhraní v výjimky a zarážky uživatelského rozhraní.

### <a name="breakpoints"></a>Zarážky
 V sadě Visual Studio 2015 je nový způsob, jak konfigurovat zarážky, který je **nastavení zarážek** okna.

 Tady je přehled hlavních zarážky oken a klávesové zkratky:

|Funkce|Umístění nabídky|Klávesová zkratka|
|-------------|-------------------|------------|
|Nová zarážka, Přepnout zarážku|**Ladění / přepněte zarážku**<br /><br /> místní nabídky v editoru / **vložit zarážku**<br /><br /> Klikněte na levý okraj|F9|
|Nová zarážka funkce|**Ladění / Nová zarážka / funkce zarážky**|V sadě Visual Studio 2015 RTM (s žádné aktualizace) použijte kombinaci kláves ALT + F9, B<br /><br /> V aplikaci Visual Studio 2015 Update 1 nebo novější použijte kombinaci kláves CTRL + B|
|**Zarážky** okna|**Ladění / Windows / zarážky**|CTRL + ALT + B|
|**Nastavení zarážek**, **podmínky**|místní nabídka na zarážce, / **podmínky**|ALT + F9, C|
|**Nastavení zarážek**, **akce**|místní nabídka na zarážce, / **akce**|Žádné klávesová zkratka|

 Další informace najdete v následujících článcích:

1.  [Použití zarážek](../debugger/using-breakpoints.md)

2.  [Nové prostředí pro konfiguraci zarážek](http://blogs.msdn.com/b/visualstudioalm/archive/2014/10/06/new-breakpoint-configuration-experience.aspx)

3.  [Prostředí pro konfiguraci zarážek](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/711)

### <a name="exception-settings"></a>Nastavení výjimek
 Nové **nastavení výjimek** okno umožňuje určit druh zpracování výjimek, které chcete, aby pro jeden výjimky nebo kategorie výjimek.

|Funkce|Umístění nabídky|Klávesová zkratka|
|-------------|-------------------|------------|
|**Nastavení výjimek** okna|**Ladění / Windows / nastavení výjimek**|CTRL + ALT + E|

 Další informace najdete v následujících článcích:

1.  [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)

2.  [Nové okno výjimky](http://blogs.msdn.com/b/visualstudioalm/archive/2015/02/23/the-new-exception-settings-window-in-visual-studio-2015.aspx)

### <a name="edit-and-continue"></a>Upravit a pokračovat
 V sadě Visual Studio 2015, můžete nastavit upravit a pokračovat v **nástroje / Možnosti / ladění / Obecné** stránky. V předchozích verzích se tato nastavení v kategorii samostatné možnosti.

### <a name="attach-to-process"></a>Připojit k procesu
 V sadě Visual Studio 2015 připojit k procesu příkaz je k dispozici pouze v nabídce ladění. V předchozí verzi kdyby byl k dispozici v nabídce Nástroje. CTRL + ALT + P klávesová zkratka funguje ve všech verzích.

## <a name="see-also"></a>Viz také
 [Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)
