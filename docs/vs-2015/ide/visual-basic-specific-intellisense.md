---
title: IntelliSense – konkrétní Visual Basic | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c6895abd85a4394e4ddcaebcd6f09bc0a39936cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663021"
---
# <a name="visual-basic-specific-intellisense"></a>Specifické pro jazyk Visual Basic IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Basic Editor zdrojového kódu nabízí následující funkce technologie IntelliSense:

- Tipy k syntaxi

     V popisech syntaxe se zobrazuje syntaxe příkazu, který píšete. To je užitečné pro příkazy, jako je například [Declare](https://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1).

## <a name="automatic-completion"></a>Automatické dokončování

- Dokončení u různých klíčových slov

   Pokud například zadáte `goto` a mezeru, IntelliSense zobrazí v rozevírací nabídce seznam definovaných popisků. Mezi další podporovaná klíčová slova patří,, `Exit` `Implements` `Option` a `Declare` .

- Dokončení `Enum` a `Boolean`

   Pokud příkaz bude odkazovat na člen výčtu, IntelliSense zobrazí seznam členů `Enum` . Pokud příkaz bude odkazovat na `Boolean` , technologie IntelliSense zobrazí rozevírací nabídku true-false.

  Dokončení může být vypnuto ve výchozím nastavení tím, že se na stránce **Obecné** vlastnosti ve složce **Visual Basic** odhlásí **Automatické seznam členů** .

  Dokončení můžete vyvolat ručně vyvoláním členů seznamu, kompletního slova nebo ALT + šipka vpravo. Další informace najdete v tématu [použití technologie IntelliSense](../ide/using-intellisense.md).

## <a name="intellisense-in-zone"></a>IntelliSense v zóně
 Technologie IntelliSense v zóně pomáhá Visual Basic vývojářům, kteří potřebují nasazovat aplikace přes [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a jsou omezeny na nastavení částečné důvěryhodnosti. Tato funkce:

- Umožňuje zvolit oprávnění, se kterými bude aplikace běžet.

- Zobrazit rozhraní API ve zvolené zóně jako dostupné v seznamech členů a zobrazit rozhraní API, která vyžadují další oprávnění jako nedostupná.

  Další informace najdete v tématu [zabezpečení přístupu kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="see-also"></a>Viz také
 [Pomocí technologie IntelliSense](../ide/using-intellisense.md)
