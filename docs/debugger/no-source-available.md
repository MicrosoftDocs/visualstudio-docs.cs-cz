---
title: Není k dispozici žádný zdroj | Microsoft Docs
description: Přečtěte si, co můžete dělat, když projekt nemá zdrojový kód pro kód, který chcete zobrazit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9993c4482d20393a3ca46d9afcd0a8ec1b13f65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942032"
---
# <a name="no-source-available"></a>Žádný zdroj není k dispozici.
Projekt neobsahuje zdrojový kód pro kód, který se pokoušíte zobrazit. Obvyklou příčinou je dvojité kliknutí na modul, který nemá zdrojový kód v okně **zásobník volání** nebo v **okně vlákna**. Můžete pokračovat v ladění, ale nemůžete použít zdrojové okno k nastavování zarážek a provádění dalších akcí v tomto umístění. Pokud potřebujete nastavit zarážku, použijte místo toho okno zpětného **překladu** .

 Na stránkách vlastností řešení můžete změnit adresáře, ve kterých ladicí program vyhledává zdrojové soubory, a sdělit ladicímu programu, že má ignorovat vybrané zdrojové soubory. Viz [dialogové okno ladit zdrojové soubory, společné vlastnosti, stránky vlastností řešení](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 Vyhledat **zdrojový kód** Kliknutím na tento odkaz otevřete dialogové okno, ve kterém můžete vyhledat zdrojový kód.

 **Zobrazit zpětný překlad** Spustí **zpětný překlad okna**.

 **Vždy zobrazit zpětný překlad pro chybějící zdrojové soubory** Tuto možnost vyberte, pokud chcete automaticky zobrazit **okno zpětný překlad** , když není k dispozici žádný zdroj. Toto nastavení lze také změnit v dialogovém okně **Možnosti** , kategorie **ladění** , **Obecné** , výběrem nebo zrušením zaškrtnutí **Zobrazit zpětný překlad, pokud není k dispozici zdroj**.

## <a name="see-also"></a>Viz také
- [Ladit zdrojové soubory, společné vlastnosti, stránky vlastností řešení – dialogové okno](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (rozšíření ladění SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)