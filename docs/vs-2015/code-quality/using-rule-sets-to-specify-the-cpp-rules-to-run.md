---
title: Použití sad pravidel k určení pravidel C++ ke spuštění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277864"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Použití sad pravidel k určování pravidel C++ pro spuštění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] a [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] můžete vytvořit a upravit vlastní *sadu pravidel* tak, aby splňovala konkrétní požadavky projektu spojené s analýzou kódu. Chcete-li vytvořit vlastní sadu pravidel jazyka C++, projekt C/C++ musí být otevřen v integrovaném vývojovém prostředí sady Visual Studio. Pak otevřete standardní sadu pravidel v editoru sad pravidel a pak přidejte nebo odeberte specifická pravidla a volitelně změňte akci, ke které dojde, když analýza kódu zjistí, že pravidlo bylo porušeno.  
  
 Pokud chcete vytvořit novou vlastní sadu pravidel, uložte ji pomocí nového názvu souboru. Vlastní sada pravidel je automaticky přiřazena k projektu.  
  
## <a name="opening-the-rule-set-editor"></a>Otevření editoru sad pravidel  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Vytvoření vlastního pravidla z jedné existující sady pravidel  
  
1. V Průzkumník řešení otevřete místní nabídku pro projekt a poté zvolte možnost **vlastnosti**.  
  
2. Na kartě **vlastnosti** klikněte na možnost **Analýza kódu**.  
  
3. V rozevíracím seznamu **sada pravidel** proveďte jednu z následujících akcí:  
  
   - Vyberte sadu pravidel, kterou chcete upravit.  
  
     \- ani  
  
   - Zvolte **\<Browse...>** , chcete-li zadat existující sadu pravidel, která není v seznamu.  
  
4. Zvolením možnosti **otevřít** zobrazte pravidla v editoru sad pravidel.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Úprava sady pravidel v editoru sad pravidel  
  
- Chcete-li změnit zobrazovaný název sady pravidel, klikněte v nabídce **zobrazení** na příkaz **Vlastnosti okno**. Do pole **název** zadejte zobrazovaný název. Všimněte si, že zobrazovaný název se může lišit od názvu souboru.  
  
- Pokud chcete přidat všechna pravidla skupiny do vlastní sady pravidel, zaškrtněte políčko u dané skupiny. Chcete-li odebrat všechna pravidla skupiny, zrušte zaškrtnutí políčka.  
  
- Chcete-li přidat konkrétní pravidlo do sady vlastních pravidel, zaškrtněte políčko pravidla. Pokud chcete pravidlo ze sady pravidel odebrat, zrušte zaškrtnutí políčka.  
  
- Chcete-li změnit akci povedenou při porušení pravidla při analýze kódu, zvolte pole **Akce** pro pravidlo a pak zvolte jednu z následujících hodnot:  
  
     **Warn** – vygeneruje upozornění.  
  
     **Chyba** – vygeneruje chybu.  
  
     **None** – zakáže pravidlo. Tato akce je stejná jako odebrání pravidla ze sady pravidel.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Seskupení, filtrování nebo změna polí v editoru sad pravidel pomocí panelu nástrojů editoru sad pravidel  
  
- Chcete-li rozšířit pravidla všech skupin, vyberte možnost **Rozbalit vše**.  
  
- Pokud chcete pravidla sbalit ve všech skupinách, klikněte na **Sbalit vše**.  
  
- Chcete-li změnit pole, podle kterého jsou pravidla seskupena, vyberte pole ze seznamu **Seskupit podle** . Chcete-li zobrazit pravidla Neseskupená, vyberte možnost **\<None>** .  
  
- Chcete-li přidat nebo odebrat pole ve sloupcích pravidla, vyberte možnost **Možnosti sloupců**.  
  
- Pokud chcete skrýt pravidla, která se nevztahují na aktuální řešení, vyberte **Skrýt pravidla, která se nevztahují na aktuální řešení**.  
  
- Chcete-li přepínat mezi zobrazením a skrytím pravidel, kterým je přiřazena akce chyba, vyberte možnost **Zobrazit pravidla, která mohou generovat chyby analýzy kódu**.  
  
- Chcete-li přepínat mezi zobrazením a skrytím pravidel, která jsou přiřazena k akci upozornění, vyberte možnost **Zobrazit pravidla, která mohou generovat upozornění analýzy kódu**.  
  
- Chcete-li přepínat mezi zobrazením a skrytím pravidel, která jsou přiřazena k akci **none** , vyberte možnost **Zobrazit pravidla, která nejsou povolena**.  
  
- Chcete-li přidat nebo odebrat výchozí sady pravidel Microsoft pro aktuální sadu pravidel, vyberte možnost **Přidat nebo odebrat podřízené sady pravidel**.
