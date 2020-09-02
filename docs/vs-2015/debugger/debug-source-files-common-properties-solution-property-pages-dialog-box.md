---
title: Ladění zdrojových souborů, společných vlastností, stránek vlastností řešení – dialogové okno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47fb2511e39153753a2c27483dd6ac96c26c9e83
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143034"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Ladění zdrojových souborů, společná nastavení, dialogové okno stránek vlastností řešení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato stránka vlastností určuje, kde bude ladicí program při ladění řešení hledat zdrojové soubory.  
  
 Chcete-li získat přístup ke stránce vlastností **zdrojové soubory ladění** , klikněte pravým tlačítkem myši na řešení v **Průzkumník řešení** a v místní nabídce vyberte možnost **vlastnosti** . Rozbalte složku **Společná nastavení** a klikněte na stránku **zdrojové soubory ladění** .  
  
 **Adresáře obsahující zdrojový kód**  
 Obsahuje seznam adresářů, ve kterých ladicí program vyhledává zdrojové soubory při ladění řešení. Prohledají se také podadresáře určených adresářů.  
  
 **Nehledat tyto zdrojové soubory**  
 Zadejte názvy všech souborů, které nechcete, aby ladicí program četl. Pokud ladicí program nalezne jeden z těchto souborů v jednom z výše uvedených adresářů, bude ho ignorovat. Pokud se dialogové okno **Najít zdroj** objeví během ladění a, kliknete na **Zrušit**, soubor, který jste hledali, se přidá do tohoto seznamu, aby ladicí program nepokračoval v hledání tohoto souboru.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
