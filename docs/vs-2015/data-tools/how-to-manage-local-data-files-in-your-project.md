---
title: 'Postupy: Správa lokálních datových souborů v projektu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.LocalConnectionConverter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- mdf files
- local data
- .mdb files
- .mdf files
- data [Visual Studio], local
- mdb files
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 16e2d38dda97bd8a7f130254b2f23be9f17e0ac4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49271372"
---
# <a name="how-to-manage-local-data-files-in-your-project"></a>Postupy: Správa lokálních datových souborů ve vašem projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Místní databázový soubor může být zahrnut jako soubor v projektu. Při prvním připojení k místnímu databázovému souboru můžete vytvořit kopii ve vašem projektu nebo připojit k existujícímu souboru v aktuálním umístění. Pokud se připojíte k existujícímu souboru, zůstane v původním umístění. Pokud budete chtít zkopírovat soubor do projektu, Visual Studio vytvoří kopii, přidá do vašeho projektu a upraví připojení tak, aby odkazoval na kopii. Další připojení, například v Průzkumníku serveru jsou také upravit.  
  
 Výchozí nastavení vlastnosti závisí na typu souboru databáze, kterou používáte. Chování **kopírovat do výstupního adresáře** vlastnost se nevztahuje na Web nebo projekty C++.  
  
 Během vývoje můžete zjistit, jaký vliv kódu v databázi bez provedení trvalých změn. Můžete to udělat nastavením **kopírovat do výstupního adresáře** vlastnost souboru na hodnotu true. Pokaždé, když sestavení projektu, nebo stiskněte klávesu F5, soubor je zkopírován do složky bin a změn do tohoto souboru, nikoli pro soubor v kořenové složce vašeho projektu. Soubor databáze v kořenové složce projektu se změní pouze při úpravách schématu databáze nebo data s využitím **Průzkumníka serveru**, **Průzkumník databáze** nebo jiného okna nástroje.  
  
 Následující tabulka popisuje nastavení **kopírovat do výstupního adresáře** vlastnost.  
  
|Nastavení|Chování|  
|-------------|--------------|  
|**Kopírovat, pokud je novější** (výchozí nastavení pro soubory SDF)|Databázový soubor je zkopírován z adresáře projektu do **bin** directory první čas sestavení projektu. Následně pokaždé při sestavení projektu, **datum změny** se porovnává vlastnost souborů. Pokud soubor ve složce projektu je novější, je zkopírován do **bin** složek, nahrazení souboru, který je aktuálně existuje. Pokud soubor v **bin** složka je novější, nejsou zkopírovány žádné soubory. Toto nastavení zachovává jakékoli změny provedené v datech za běhu, což znamená, že při každém spuštění aplikace a uložit změny dat, jsou tyto změny viditelné při příštím spuštění aplikace. **Upozornění:** nedoporučujeme tuto možnost pro soubory .mdb nebo mdf. Soubor databáze se může změnit i v případě, že k datům nebudou provedeny žádné změny. Jednoduše otevřete připojení datového souboru (například tak, že rozbalíte **tabulky** uzel v **Průzkumníka serveru**) lze označit jako novější.|  
|**Vždy kopírovat** (výchozí nastavení pro soubory MDF a MDB)|Databázový soubor je zkopírován z adresáře projektu do adresáře/Bin při každém sestavení aplikace. Proto pokud sestavíte aplikaci a uložit změny do souboru v adresáři/Bin, tyto změny přepsány při příštím původní soubor je zkopírován do adresáře/Bin.|  
|**Nekopírovat**|Soubor není zkopírován ani přepsán systémem projektu. Pokud použijete toto nastavení, musíte ručně zkopírovat soubor z adresáře projektu do výstupního adresáře.|  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-respond-to-the-local-database-file-dialog-box"></a>Reakce na dialogové okno místní databázový soubor  
  
-   Klikněte na tlačítko **Ano** Pokud chcete, aby sada Visual Studio zkopírovala databázový soubor do projektu a upravte připojení tak, aby odkazoval na kopii ve vašem projektu. Další informace o práci se soubory databáze do projektu naleznete v tématu [Local Data Overview](../data-tools/local-data-overview.md).  
  
-   Klikněte na tlačítko **ne** Pokud nechcete, aby aplikace Visual Studio zkopírovala databázový soubor do projektu. Místo toho spojovací body do souboru v původním umístění a soubor databáze nebudou přidány jako soubor do projektu.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Připojování k datům v lokálního databázového souboru (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Připojení k datům v databázi Accessu (model Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)