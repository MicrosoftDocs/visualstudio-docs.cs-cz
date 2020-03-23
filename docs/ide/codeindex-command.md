---
title: CodeIndex, příkaz
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command-line tools [Team Foundation Server]
- TFSConfig
- CodeIndex command [Team Foundation Server]
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bd2a6cc947c5f52212029bebe590d59906f5aee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591161"
---
# <a name="codeindex-command"></a>CodeIndex, příkaz

Příkaz **CodeIndex** slouží ke správě indexování kódu na serveru Team Foundation Server. Můžete například obnovit index opravit CodeLens informace nebo vypnout indexování prozkoumat problémy s výkonem serveru.

## <a name="required-permissions"></a>Požadovaná oprávnění

Chcete-li použít příkaz **CodeIndex,** musíte být členem skupiny zabezpečení **Správci Team Foundation.** Viz [Oprávnění a skupiny definované pro služby Azure DevOps Services a TFS](/azure/devops/organizations/security/permissions?view=vsts).

> [!NOTE]
> I v případě, že se přihlásíte pomocí pověření pro správu, je nutné otevřít okno příkazového řádku se zvýšenými oprávněními, abyste tento příkaz spouštěli. Tento příkaz musíte také spustit z aplikační vrstvy pro Team Foundation.

## <a name="syntax"></a>Syntaxe

```cmd
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]
```

### <a name="parameters"></a>Parametry

|**Argument**|**Popis**|
|------------------| - |
|`CollectionName`|Určuje název kolekce projektu. Pokud má název mezery, uzavřete jej do uvozovek, například "Web společnosti Fabrikam".|
|`CollectionId`|Určuje identifikační číslo kolekce projektu.|
|`ServerPath`|Určuje cestu k souboru kódu.|

|**Možnost**|**Popis**|
|----------------| - |
|**/indexingStatus**|Zobrazí stav a konfiguraci služby indexování kódu.|
|**/setIndexing:**[ vypnuto &#124; &#124; keepupOnly ]|-   **zapnuto**: Začněte indexovat všechny sady změn.<br />-   **vypnuto**: Zastavte indexování všech sad změn.<br />-   **keepupOnly**: Zastavte indexování dříve vytvořených sad změn a spusťte indexování pouze nových sad změn.|
|**/ignoreList:**[ přidat &#124; odebrat &#124; odebratvšechny &#124; zobrazení ]`ServerPath`<br /><br /> Zástupný znak (*) můžete použít na začátku, na konci nebo na obou koncích cesty k serveru.|Určuje seznam souborů kódu a jejich cesty, které nechcete indexovat.<br /><br /> -   **add**: Přidejte soubor, který nechcete indexovat, do seznamu ignorovaných souborů.<br />-   **odebrat**: Odeberte soubor, který chcete indexovat, ze seznamu ignorovaných souborů.<br />-   **removeAll**: Vymažte seznam ignorovaných souborů a spusťte indexování všech souborů.<br />-   **Zobrazení**: Zobrazení všech souborů, které nejsou indexovány.|
|**/listLargeFiles [/fileCount:** `FileCount` **/minSize:** `MinSize`]|Zobrazuje zadaný počet souborů, které překračují zadanou velikost v kb. Potom můžete použít **/ignoreList** možnost vyloučit tyto soubory z indexování.|
|**/reindexAll**|Zrušte dříve indexovaná data a restartujte indexování.|
|**/destroyCodeIndex [/noPrompt]**|Odstraňte index kódu a odeberte všechna indexovaná data. Nevyžaduje potvrzení, pokud použijete **/noPrompt** možnost.|
|**/temporaryDataSizeLimit**:[ `SizeInGBs` zobrazení &#124; <> &#124; zakázat ]|Určit, kolik dočasných dat, které CodeLens vytvoří při zpracování sady změn. Výchozí limit je 2 GB.<br /><br /> -   **Zobrazení**: Zobrazí aktuální limit velikosti.<br />-   `SizeInGBs`: Změna limitu velikosti.<br />-   **zakázat**: Odeberte limit velikosti.<br /><br /> Tento limit je kontrolována před CodeLens zpracuje novou sadu změn. Pokud dočasná data překročí tento limit, CodeLens pozastaví zpracování minulých sad změn, nikoli nových. CodeLens restartuje zpracování po vyčištění dat a klesne pod tento limit. Vyčištění se spouští automaticky jednou denně. To znamená, že dočasná data mohou překročit tento limit, dokud nebude spuštěno vyčištění.|
|**/indexHistoryPeriod**:[ zobrazení `NumberOfMonths` &#124; všechny> &#124; <]|Určit, jak dlouho chcete indexovat historii změn. To má vliv na to, kolik historie CodeLens zobrazuje. Výchozí limit je 12 měsíců. To znamená, že CodeLens zobrazuje historii změn pouze za posledních 12 měsíců.<br /><br /> -   **Zobrazení**: Zobrazení aktuálního počtu měsíců.<br />-   **vše**: Indexovat všechny změny historie.<br />-   `NumberOfMonths`: Změna počtu měsíců použitých k indexování historie změn.|
|**/collectionName:**`CollectionName`|Určuje název kolekce projektu, na kterém chcete spustit příkaz **CodeIndex.** Povinné, pokud nepoužíváte **/CollectionId**.|
|**/collectionId:**`CollectionId`|Určuje identifikační číslo kolekce projektu, na kterém chcete spustit příkaz **CodeIndex.** Povinné, pokud nepoužíváte **/CollectionName**.|

## <a name="examples"></a>Příklady

> [!NOTE]
> Zde uvedené příklady společností, organizací, produktů, názvů domén, e-mailových adres, log, osob, míst a událostí jsou smyšlené.  Žádné spojení se skutečnou společností, organizací, produktem, názvem domény, e-mailovou adresou, logem, osobou, místy nebo událostmi není zamýšleno ani by nemělo být vyvozováno.

Zobrazení stavu a konfigurace indexování kódu:

```cmd
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Website"
```

Chcete-li spustit indexování všech sad změn:

```cmd
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Website"
```

Chcete-li zastavit indexování dříve vytvořených sad změn a spustit indexování pouze nových sad změn:

```cmd
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Website"
```

Vyhledání až 50 souborů, které jsou větší než 10 kB:

```cmd
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Website"
```

Chcete-li vyloučit určitý soubor z indexování a přidat jej do seznamu ignorovaných souborů:

```cmd
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Website/Catalog.cs" /collectionName:"Fabrikam Website"
```

Zobrazení všech neindexovaných souborů:

```cmd
TFSConfig CodeIndex /ignoreList:view
```

Vymazání dříve indexovaných dat a restartování indexování:

```cmd
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Website"
```

Uložení veškeré historie sady změn:

```cmd
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Website"
```

Chcete-li odebrat limit velikosti dočasných dat CodeLens a pokračovat v indexování bez ohledu na velikost dočasných dat:

```cmd
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Website"
```

Odstranění indexu kódu s potvrzením:

```cmd
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Website"
```

## <a name="see-also"></a>Viz také

- [Nalezení změn kódu a další historie pomocí CodeLensu](../ide/find-code-changes-and-other-history-with-codelens.md)
- [Správa konfigurace serveru pomocí tfsconfig](/azure/devops/server/command-line/tfsconfig-cmd)
