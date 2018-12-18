---
title: Codeindex – příkaz | Dokumentace Microsoftu
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
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9586348a1862820540613a5f191132c49fa6a74d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282357"
---
# <a name="codeindex-command"></a>CodeIndex – příkaz
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použití **CodeIndex** příkaz pro správu indexování kódu na Team Foundation Server. Můžete například chtít resetovat index pro opravu informace CodeLens nebo vypnout indexování kódu a zjistit problémy s výkonem serveru.  
  
 **Požadovaná oprávnění**  
  
 Použít **CodeIndex** příkaz, musíte být členem skupiny **správci serveru Team Foundation** skupiny zabezpečení. Zobrazit [reference k oprávněním pro Team Foundation Server](http://msdn.microsoft.com/library/39997de5-b7fb-4777-b779-07de0543abe6).  
  
> [!NOTE]
>  I když se přihlásíte s přihlašovacími údaji správce, musíte otevřít okno příkazového řádku se zvýšenými oprávněními ke spuštění tohoto příkazu. Tento příkaz musíte také spustit z aplikační vrstvy pro Team Foundation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|**Argument**|**Popis**|  
|------------------|---------------------|  
|`CollectionName`|Určuje název kolekce týmového projektu. Pokud název obsahuje mezery, uzavřete ho uvozovek, například "webové stránky Fabrikam".|  
|`CollectionId`|Určuje identifikační číslo kolekce týmového projektu.|  
|`ServerPath`|Určuje cestu k souboru kódu.|  
  
|**Možnost**|**Popis**|  
|----------------|---------------------|  
|**/indexingStatus**|Zobrazení stavu a konfigurace služby indexování kódu.|  
|**/setIndexing:**[na &#124; vypnout &#124; keepupOnly]|-   **na**: zahájení indexování všech sad změn.<br />-   **vypnout**: ukončení indexování všech sad změn.<br />-   **keepupOnly**: zastavení indexování dříve vytvořených sad změn a spuštění indexování pouze nových sad změn.|  
|**/ignoreList:**[Přidat &#124; odebrat &#124; removeAll &#124; zobrazení] `ServerPath`<br /><br /> Na začátku, konci nebo na obou koncích cesty k serveru můžete použít zástupný znak (*).|Určuje seznam souborů s kódem a jejich cesty, které nechcete indexované.<br /><br /> -   **Přidat**: přidání souboru, který nechcete indexovat do seznamu ignorovaných souborů.<br />-   **Odebrat**: odstranění souboru, který chcete indexovat ze seznamu ignorovaných souborů.<br />-   **removeAll**: vymazání seznamu ignorovaných souborů a zahájení indexování všech souborů.<br />-   **zobrazení**: Zobrazit všechny soubory, které nejsou indexovat.|  
|**/listLargeFiles [/ fileCount:** `FileCount` **/minSize:** `MinSize`]|Zobrazí zadaný počet souborů, která překračuje zadanou velikost v KB. Pak můžete použít **/ignoreList** možnost, chcete-li z indexování vyloučit tyto soubory.|  
|**/reindexAll**|Vymažte dříve indexovaná data a spusťte indexování znovu.|  
|**/destroyCodeIndex [/ noprompt]**|Smazat index kódu a odstranit všechna indexovaná data. Pokud používáte nevyžaduje potvrzení **/noprompt** možnost.|  
|**/temporaryDataSizeLimit**: [zobrazení &#124; <`SizeInGBs`> &#124; zakázat]|Určit, kolik dočasná data, která vytvoří CodeLens při zpracování sady změn. Výchozí omezení je 2 GB.<br /><br /> -   **zobrazení**: Zobrazit aktuální limit velikosti.<br />-   `SizeInGBs`: Změňte limit velikosti.<br />-   **Zakázat**: odebrání omezení velikosti.<br /><br /> Toto omezení je zaškrtnuto, než funkce CodeLens zpracuje novou sadu změn. Dočasná data, která překračuje tento limit, CodeLens pozastaví zpracování poslední sady změn, nikoli nové značky. CodeLens se restartuje po data se vyčistí a klesne pod tento limit zpracování. Čištění se spustí automaticky jednou denně. To znamená, že dočasná data, která může překročit tento limit, dokud se čištění se spustí.|  
|**/indexHistoryPeriod**: [zobrazení &#124; všechny &#124; <`NumberOfMonths`>]|Ovládací prvek, jak dlouho se má indexovat historii změn. To má vliv na tom, kolik historie CodeLens ukazuje. Výchozí limit je 12 měsíců. To znamená, že funkce CodeLens ukazuje historii změn z pouze za posledních 12 měsíců.<br /><br /> -   **zobrazení**: Zobrazit aktuální počet měsíců.<br />-   **všechny**: Index veškerá historie změn.<br />-   `NumberOfMonths`: Počet měsíců pro historii změn index změňte.|  
|**/collectionName:** `CollectionName`|Určuje název kolekce týmového projektu, ve kterém se spustí **CodeIndex** příkazu. Povinné, pokud nepoužíváte **/CollectionId**.|  
|**/collectionId:** `CollectionId`|Určuje identifikační číslo kolekce týmového projektu, ve kterém se spustí **CodeIndex** příkazu. Povinné, pokud nepoužíváte **/CollectionName**.|  
  
## <a name="examples"></a>Příklady  
  
> [!NOTE]
>  Vzorové společnosti, organizace, produkty, názvy domén, e-mailové adresy, loga, osoby, místa a události použité v ukázkách jsou smyšlené.  Žádné jejich spojení se skutečnou společností, organizaci, produktu, název domény, e-mailovou adresu, loga, osoby, místa nebo události je určena ji vyvozovat.  
  
 Chcete-li zobrazit kód stavu a konfiguraci indexování:  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 Zahájení indexování všech sad změn:  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 Chcete-li zastavit indexování dříve vytvořených sad změn a spustit indexování pouze nových sad změn:  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 K vyhledání až 50 souborů, které jsou větší než 10 KB:  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 Chcete-li z indexování vyloučit určitý soubor a přidejte do seznamu ignorovaných souborů:  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 Pokud chcete zobrazit všechny soubory, které nejsou indexována:  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 Vymažte dříve indexovaná data a znovu spustit indexování:  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 Uložte veškerá historie změn:  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 Odebrání omezení velikosti pro dočasná data CodeLens a pokračovat indexování bez ohledu na velikost dočasných dat:  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 Chcete-li odstranit kód indexu s potvrzením:  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## <a name="see-also"></a>Viz také  
 [Správa konfigurace serveru pomocí nástroje TFSConfig](http://msdn.microsoft.com/en-us/94424190-3b6b-4f33-a6b6-5807f4225b62)   
 [Nástroje příkazového řádku pro TFS](http://msdn.microsoft.com/en-us/be8c997a-b97b-4e59-97f5-04db0a601a6c)



