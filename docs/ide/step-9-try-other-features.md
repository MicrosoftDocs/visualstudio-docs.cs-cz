---
title: 'Krok 9: Vyzkoušejte jiné funkce'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 395d8512536c5ea2470eeeed1d25bd9de4c2f581
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672129"
---
# <a name="step-9-try-other-features"></a>Krok 9: Vyzkoušejte jiné funkce
Chcete-li získat další informace, zkuste změnit ikony a barvy, přidat časovač hry a zvuky. Chcete-li, aby hra byla náročnější, zkuste zvětšit hrací plochu a upravte časovač.  
  
 Chcete-li stáhnout úplnou verzi vzorku, přečtěte si téma [kompletní odpovídající her ukázkový kurz](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
## <a name="to-try-other-features"></a>Vyzkoušení dalších funkcí  

-   Nahraďte ikony a barvy těmi, které zvolíte.  

    > [!TIP]
    >  Podívejte se na popisku [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) vlastnost.  

-   Přidejte časovač hry, který sleduje, jak dlouho hráči trvá, než vyhraje.  

    > [!TIP]
    >  K tomuto účelu můžete přidat popisek se zobrazí uplynulý čas na výše uvedeného formuláře <xref:System.Windows.Forms.TableLayoutPanel>, a přidat další časovač na formuláři pro sledování času. Použijte kód ke spuštění časovače, když hráč zahájí hru, a zastavení časovače, jakmile hráč spojí poslední dvě ikony.  

-   Pokud hráč najde shodu, přidejte zvuk, jiný zvuk, když hráč odkryje dvě ikony, které neodpovídají, a třetí zvuk, když program znovu skryje ikony.  

    > [!TIP]
    >  Chcete-li přehrát zvuky, můžete použít <xref:System.Media> oboru názvů. Zobrazit [přehrát zvuky v aplikaci Windows Forms (C#)](http://youtu.be/qOh4ooHg1UU) nebo [pokyny pro hru zvuku v jazyce Visual Basic](http://youtu.be/-4oPDeQrtMs) Další informace.  
  
-   Udělejte hru obtížnější tím, že zvětšíte hrací plochu.  

    > [!TIP]
    >  Budete potřebovat víc než jen přidat řádky a sloupce do kontejneru TableLayoutPanel – bude také nutné zvážit počet ikon, které vytvoříte.  

-   Udělejte hru náročnější tím, že skryjete první ikonu, pokud je hráč příliš pomalý a nezvolí druhou ikonu do vypršení určitého časového limitu.  

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Pokud si nevíte rady nebo máte otázky k programování, můžete zveřejnit svůj dotaz na jednom z diskuzních fór MSDN. Zobrazit [fórum Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) a [fórum Visual C#](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral).
  
-   K dispozici jsou užitečné bezplatné video výukové materiály. Další informace o programování v jazyce Visual Basic najdete v tématu [základy jazyka Visual Basic: vývoj pro naprosté začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Další informace o programování v jazyce Visual C# najdete v tématu [Základy C#: vývoj pro naprosté začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 8: Přidejte metodu k ověření, zda hráč zvítězil](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
