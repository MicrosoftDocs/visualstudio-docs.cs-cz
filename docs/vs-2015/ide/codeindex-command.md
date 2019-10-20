---
title: Příkaz CodeIndex – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 070106dc4db0f5200c1346bbbf8c0b653aa104e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619669"
---
# <a name="codeindex-command"></a>CodeIndex – příkaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí příkazu **CodeIndex –** můžete spravovat indexování kódu na Team Foundation Server. Můžete například chtít obnovit index, aby opravil CodeLens informace, nebo vypnout indexování a prozkoumat problémy s výkonem serveru.

 **Požadovaná oprávnění**

 Chcete-li použít příkaz **CodeIndex –** , musíte být členem skupiny zabezpečení **Správci Team Foundation** . Viz [referenční informace k oprávněním pro Team Foundation Server](https://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6).

> [!NOTE]
> I v případě, že se přihlašujete pomocí pověření správce, je nutné otevřít okno příkazového řádku se zvýšenými oprávněními ke spuštění tohoto příkazu. Tento příkaz musíte spustit také z aplikační vrstvy pro Team Foundation.

## <a name="syntax"></a>Syntaxe

```
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

#### <a name="parameters"></a>Parametry

|**Argument**|**Popis**|
|------------------|---------------------|
|`CollectionName`|Určuje název kolekce týmového projektu. Pokud název obsahuje mezery, uzavřete název do uvozovek, například "Fabrikam web".|
|`CollectionId`|Určuje identifikační číslo kolekce týmového projektu.|
|`ServerPath`|Určuje cestu k souboru kódu.|

|**Nastavení**|**Popis**|
|----------------|---------------------|
|**/indexingStatus**|Zobrazit stav a konfiguraci služby indexování kódu.|
|**/setIndexing:** [on &#124; off &#124; keepupOnly]|-    **:** začátek indexování všech sad změn.<br />-   **vypnuto**: zastavit indexování všech sad změn.<br />-   **keepupOnly**: Zastavte indexování dříve vytvořených sad změn a zahajte indexování pouze nových sad změn.|
|**/ignorelist:** [přidat &#124; odebrání &#124; RemoveAll &#124; zobrazení] `ServerPath`<br /><br /> Můžete použít zástupný znak (*) na začátku, na konci nebo na obou koncích cesty serveru.|Určuje seznam souborů kódu a jejich cesty, které nechcete indexovat.<br /><br /> -   **Přidat**: přidejte soubor, který nechcete indexovat, do seznamu ignorovaných souborů.<br />-   **Odebrat**: ze seznamu ignorovaných souborů odeberte soubor, který chcete indexovat.<br />-   **RemoveAll**: Vymažte seznam ignorovaných souborů a spusťte indexování všech souborů.<br />-   **zobrazení**: Zobrazit všechny soubory, které nejsou indexovány.|
|**/listLargeFiles [/FileCount:** `FileCount` **/minSize:** `MinSize`]|Zobrazuje zadaný počet souborů, které přesahují zadanou velikost v KB. Pak můžete použít možnost **/ignorelist** k vyloučení těchto souborů z indexování.|
|**/reindexAll**|Vymažte dříve indexovaná data a znovu spusťte indexování.|
|**/destroyCodeIndex [/noPrompt]**|Odstraňte index kódu a odeberte všechna indexovaná data. Nevyžaduje potvrzení, pokud použijete možnost **/NoPrompt** .|
|**/temporaryDataSizeLimit**: [zobrazení &#124; < `SizeInGBs` > &#124; zakázat]|Určuje, kolik dočasných dat, která CodeLens vytvoří při zpracování sad změn. Výchozí limit je 2 GB.<br /><br /> -   **zobrazení**: Zobrazit omezení aktuální velikosti.<br />-    `SizeInGBs`: Změňte limit velikosti.<br />-   **Zakázat**: odebrat omezení velikosti.<br /><br /> Toto omezení je zaškrtnuto před tím, než CodeLens zpracuje novou sadu změn. Pokud dočasná data překročí tento limit, CodeLens pozastaví zpracování minulých sad změn, nikoli nových. CodeLens restartuje zpracování po vyčištění dat a klesne pod tento limit. Automatické čištění se spustí jednou denně. To znamená, že dočasná data mohou překročit tento limit, dokud nebude spuštěno čištění.|
|**/indexHistoryPeriod**: [zobrazit &#124; všechny &#124; < `NumberOfMonths` >]|Určuje, jak dlouho se má indexovat historie změn indexovat. To má vliv na to, kolik historie CodeLens ukazuje. Výchozí limit je 12 měsíců. To znamená, že CodeLens zobrazuje historii změn jenom za posledních 12 měsíců.<br /><br /> -   **zobrazení**: zobrazí aktuální počet měsíců.<br />-   **All**: indexovat veškerou historii změn.<br />-    `NumberOfMonths`: změňte počet měsíců použitých k indexování historie změn.|
|**/CollectionName:** `CollectionName`|Určuje název kolekce týmového projektu, na které se má spustit příkaz **CodeIndex –** . Vyžaduje se, pokud nepoužíváte **/CollectionID**.|
|**/collectionId:** `CollectionId`|Určuje identifikační číslo kolekce týmového projektu, ve kterém se má spustit příkaz **CodeIndex –** . Vyžaduje se, pokud nepoužíváte **/CollectionName**.|

## <a name="examples"></a>Příklady

> [!NOTE]
> Ukázkové společnosti, organizace, produkty, názvy domén, e-mailové adresy, loga, osoby, místa a události použité v ukázkách jsou smyšlené.  Žádná spojitost se skutečnou společností, organizací, produktem, názvem domény, e-mailovou adresou, logem, osobou, místem a událostmi není zamýšlená nebo by se měla odvodit.

 Chcete-li zobrazit stav a konfiguraci indexování kódu:

```
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"
```

 Spuštění indexování všech sad změn:

```
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"
```

 Zastavení indexování dříve vytvořených sad změn a zahájení indexování pouze nových sad změn:

```
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"
```

 Pokud chcete najít až 50 souborů, které jsou větší než 10 KB:

```
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"
```

 Vyloučení konkrétního souboru z indexování a jeho přidání do seznamu ignorovaných souborů:

```
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"
```

 Chcete-li zobrazit všechny soubory, které nejsou indexovány:

```
TFSConfig CodeIndex /ignoreList:view
```

 Chcete-li vymazat dříve indexovaná data a znovu spustit indexování:

```
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"
```

 Uložení historie všech sad změn:

```
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"
```

 Chcete-li odebrat omezení velikosti CodeLens dočasných dat a pokračovat v indexování bez ohledu na velikost dočasného data:

```
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"
```

 Postup odstranění indexu kódu s potvrzením:

```
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"
```

## <a name="see-also"></a>Viz také
 [Správa konfigurace serveru pomocí](https://msdn.microsoft.com/94424190-3b6b-4f33-a6b6-5807f4225b62) [nástrojů příkazového řádku TFSConfig pro TFS](https://msdn.microsoft.com/be8c997a-b97b-4e59-97f5-04db0a601a6c)
