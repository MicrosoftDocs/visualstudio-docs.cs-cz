---
title: Zdrojové soubory ladění/stránky vlastností řešení
description: Kliknutím pravým tlačítkem myši na své řešení v Průzkumník řešení a výběrem vlastností > společných vlastností se dostanete na stránku vlastností zdrojové soubory ladění v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10818f473dec392364832cdc2f5215197ef4627f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873168"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Ladění zdrojových souborů, společná nastavení, dialogové okno stránek vlastností řešení
Tato stránka vlastností určuje, kde bude ladicí program při ladění řešení hledat zdrojové soubory.

 Chcete-li získat přístup ke stránce vlastností **zdrojové soubory ladění** , klikněte pravým tlačítkem myši na řešení v **Průzkumník řešení** a v místní nabídce vyberte možnost **vlastnosti** . Rozbalte složku **Společná nastavení** a klikněte na stránku **zdrojové soubory ladění** .

 **Adresáře obsahující zdrojový kód** Obsahuje seznam adresářů, ve kterých ladicí program vyhledává zdrojové soubory při ladění řešení. Prohledají se také podadresáře určených adresářů.

 **Nehledat tyto zdrojové soubory** Zadejte názvy všech souborů, které nechcete, aby ladicí program četl. Pokud ladicí program nalezne jeden z těchto souborů v jednom z výše uvedených adresářů, bude ho ignorovat. Pokud se dialogové okno **Najít zdroj** objeví během ladění a, kliknete na **Zrušit**, soubor, který jste hledali, se přidá do tohoto seznamu, aby ladicí program nepokračoval v hledání tohoto souboru.

## <a name="see-also"></a>Viz také

- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)