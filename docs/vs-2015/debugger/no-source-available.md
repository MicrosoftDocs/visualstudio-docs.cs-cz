---
title: Není k dispozici žádný zdroj | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69ea9c3a41f83b9c06dc18d6da1f859017f12ca5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697798"
---
# <a name="no-source-available"></a>Žádný zdroj není k dispozici.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projekt neobsahuje zdrojový kód pro kód, který se pokoušíte zobrazit. Obvyklou příčinou je dvojité kliknutí na modul, který nemá zdrojový kód v okně **zásobník volání** nebo v **okně vlákna**. Můžete pokračovat v ladění, ale nemůžete použít zdrojové okno k nastavování zarážek a provádění dalších akcí v tomto umístění. Pokud potřebujete nastavit zarážku, použijte místo toho okno zpětného **překladu** .  
  
 Na stránkách vlastností řešení můžete změnit adresáře, ve kterých ladicí program vyhledává zdrojové soubory, a sdělit ladicímu programu, že má ignorovat vybrané zdrojové soubory. Viz [dialogové okno ladit zdrojové soubory, společné vlastnosti, stránky vlastností řešení](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Vyhledat zdrojový kód**  
 Kliknutím na tento odkaz otevřete dialogové okno, ve kterém můžete vyhledat zdrojový kód.  
  
 **Zobrazit zpětný překlad**  
 Spustí **zpětný překlad okna**.  
  
 **Vždy zobrazit zpětný překlad pro chybějící zdrojové soubory**  
 Tuto možnost vyberte, pokud chcete automaticky zobrazit **okno zpětný překlad** , když není k dispozici žádný zdroj. Toto nastavení lze také změnit v dialogovém okně **Možnosti** , kategorie **ladění** , **Obecné** , výběrem nebo zrušením zaškrtnutí **Zobrazit zpětný překlad, pokud není k dispozici zdroj**.  
  
## <a name="see-also"></a>Viz také  
 [Ladit zdrojové soubory, společné vlastnosti, stránky vlastností řešení – dialogové okno](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Zadat symbol (PDB) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (rozšíření ladění SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
