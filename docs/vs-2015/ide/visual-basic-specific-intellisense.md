---
title: Specifické pro jazyk Visual Basic IntelliSense | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7fbeae534915863ec8a49e529bef4f6eb0c0fcb0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49852489"
---
# <a name="visual-basic-specific-intellisense"></a>Specifické pro jazyk Visual Basic IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor zdrojového kódu jazyka Visual Basic nabízí následující funkce IntelliSense:  
  
-   Syntaxe tipy  
  
     Syntaxe tipy zobrazení syntaxe příkazu, který píšete. To je užitečné pro příkazy, jako [Declare](http://msdn.microsoft.com/library/d3f21fb0-b804-4c99-97ed-583b23894cf1).  
  
## <a name="automatic-completion"></a>Automatické dokončování  
  
- Dokončení různých klíčových slov  
  
   Pokud zadáte například `goto` a mezerou, technologie IntelliSense zobrazí seznam popisků definované v rozevírací nabídce. Zahrnout další podporované klíčová slova `Exit`, `Implements`, `Option`, a `Declare`.  
  
- Dokončení `Enum` a `Boolean`  
  
   Pokud příkaz bude odkazovat na člena výčtu, technologie IntelliSense zobrazí seznam členů `Enum`. Pokud příkaz bude odkazovat `Boolean`, technologie IntelliSense se zobrazí rozevírací nabídky true na false.  
  
  Dokončení může být ve výchozím nastavení vypnuta odznačením **automatický seznam členů** z **Obecné** stránku vlastností v **jazyka Visual Basic** složky.  
  
  Dokončení lze vyvolat ručně vyvoláním seznam členů, úplné slovo nebo ALT + Šipka vpravo. Další informace najdete v tématu [pomocí technologie IntelliSense](../ide/using-intellisense.md).  
  
## <a name="intellisense-in-zone"></a>Technologie IntelliSense v zóně  
 Technologie IntelliSense v zóně pomáhá vývojáře jazyka Visual Basic, kteří potřebují nasazovat aplikace prostřednictvím [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] a jsou omezeny na nastavení částečným vztahem důvěryhodnosti. Tuto funkci:  
  
- Umožní vám vybrat oprávnění, která bude aplikace spuštěna s.  
  
- Rozhraní API zobrazení ve vybrané jako dostupné v seznamu členů zóny a zobrazit rozhraní API, která vyžadují další oprávnění jako nedostupné.  
  
  Další informace najdete v tématu [Code Access Security for ClickOnce Applications](../deployment/code-access-security-for-clickonce-applications.md).  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu IntelliSense](../ide/using-intellisense.md)



