---
title: Kontextové nabídky v Průzkumníku schémat XML
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f7224ca09588858398a0f45c35008ddd5ba0af71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592890"
---
# <a name="context-menus-xml-schema-explorer"></a>Kontextové nabídky (Průzkumník schémat XML)

Kontextová nabídka je nabídka, která se zobrazí po kliknutí pravým tlačítkem myši na něco. Následující položky kontextové nabídky slouží k provádění vyhledávání specifických pro konkrétní schéma a dalších operací.

## <a name="node-type-schema-set"></a>Typ uzlu: sada schémat

Následující tabulka popisuje možnosti, které jsou k dispozici pro uzel sady schémat.

|Možnost|Popis|
|-|-----------------|
|**Zobrazit nejpravděpodobnější kořenové prvky**|Vyhledá a zvýrazní všechny globální prvky, které nejsou odkazovány z globálních prvků kromě sebe samé.|
|**Zobrazit globální typy**|Vyhledá a zvýrazní všechny globální typy v sadě schémat.|
|**Zobrazit globální prvky**|Vyhledá a zvýrazní všechny globální prvky v sadě schémat.|
|**Okno vlastností**|Otevře okno **vlastnosti** (Pokud ještě není otevřené). V tomto okně se zobrazují informace o uzlu.|

## <a name="node-type-namespace"></a>Typ uzlu: obor názvů
Následující tabulka popisuje možnosti, které jsou k dispozici pro uzel oboru názvů.

|Možnost|Popis|
|-|-----------------|
|**Zobrazit všechny příchozí odkazy**|Najde a zvýrazní soubory, které importují vybraný obor názvů.|
|**Zobrazit všechny odchozí odkazy**|Pro každý soubor ve vybraném oboru názvů najde a zvýrazní následující:<br /><br /> -Všechny obory názvů odkazované v příkazech importu bez `schemaLocation` atributu.<br />– Všechny soubory v oborech názvů jiné než vybrané, které jsou zadány v `schemaLocation` atributu v příkazech import a include.|
|**Zobrazit globální typy**|Najde a zvýrazní všechny globální typy ve vybraném oboru názvů.|
|**Zobrazit globální prvky**|Vyhledá a zvýrazní všechny globální prvky ve vybraném oboru názvů.|
|**Okno vlastností**|Otevře okno **vlastnosti** (Pokud ještě není otevřené). V tomto okně se zobrazují informace o uzlu.|

## <a name="node-type-file"></a>Typ uzlu: soubor
Následující tabulka popisuje možnosti, které jsou k dispozici pro uzel souboru.

|Možnost|Popis|
|-|-----------------|
|**Zobrazit všechny příchozí odkazy**|Vyhledá a zvýrazní všechny soubory, které určují vybraný soubor v `schemaLocation` atributech příkazů include a import.|
|**Zobrazit všechny odchozí odkazy**|Najde a zvýrazní následující:<br /><br /> – Všechny obory názvů zadané v atributech oboru názvů pro všechny příkazy import, které nemají `schemaLocation` atribut.<br />– Všechny soubory zadané v `schemaLocation` atributech všech příkazů import a zahrnout.|
|**Zobrazit globální typy**|Vyhledá a zvýrazní všechny globální typy v tomto souboru.|
|**Zobrazit globální prvky**|Vyhledá a zvýrazní všechny globální prvky v tomto souboru.|
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položka, která je vybrána v Průzkumníku schémat XML, bude také vybrána v editoru XML.|
|**Okno vlastností**|Otevře okno **vlastnosti** (Pokud ještě není otevřené). V tomto okně se zobrazují informace o uzlu.|

## <a name="all-global-node-types"></a>Všechny typy globálních uzlů
Následující tabulka popisuje možnosti, které jsou k dispozici pro všechny globální uzly.

|Možnost|Popis|
|-|-----------------|
|**Zobrazit v zobrazení grafu**|Otevře zobrazení grafu. Pokud vybraný uzel není v pracovním prostoru, přidá ho do pracovního prostoru a vybere uzel.|
|**Zobrazit v zobrazení modelu obsahu**|Otevře zobrazení modelu obsahu. Pokud vybraný uzel není v pracovním prostoru, přidá ho do pracovního prostoru a vybere uzel.|
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položka, která je vybrána v Průzkumníku schémat XML, bude také vybrána v editoru XML.|
|**Okno vlastností**|Otevře okno **vlastnosti** (Pokud ještě není otevřené). V tomto okně se zobrazují informace o uzlu.|

## <a name="node-type-element"></a>Typ uzlu: element
Kromě možností globálního uzlu popsaných výše má kontextová nabídka pro uzly elementu následující možnosti:

|Možnost|Popis|
|-|-----------------|
|**Přejít na definici typu**|Přejde k definici typu vybraného elementu. To platí v případě, že typ, který je použit pro prvek, je globální typ.|
|**Přejít k původnímu elementu**|V případě odkazů na prvky přejdete na skutečnou definici elementu.|
|**Zobrazit všechny odkazy**|U globálních elementů najde a zvýrazní všechny odkazy (prvky, které mají `ref="selectedElement"` ) na vybraný prvek.|
|**Zobrazit členy substituční skupiny**|U hlav substituční skupiny najde a zvýrazní všechny prvky, které jsou členy skupiny nahrazení, které je vybraný element členem. Zobrazuje se přímo a nepřímá účastníci.|
|**Zobrazit hlavičky substitučních skupin**|U globálních prvků, které jsou členy substituční skupiny, najde a zvýrazní všechny přímé a nepřímé hlavy pro vybraný prvek, například následující:<br /><br /> -Pro vybraný element je určena hlava substituční skupiny.<br />-V elementu Head je určen hlavní hlava (substituční skupina).|
|**Generovat vzorový kód XML**|K dispozici pouze pro globální prvky. Vygeneruje vzorový soubor XML pro globální prvek.|

## <a name="node-type-global-types"></a>Typ uzlu: globální typy
Kromě možností globálního uzlu popsaných výše má kontextová nabídka pro uzly globálního typu následující možnosti:

|Možnost|Popis|
|-|-----------------|
|**Zobrazit základní typ**|Pokud je vybraný typ odvozen z globálního typu, přejde na základní typ vybraného typu.|
|**Zobrazit všechny odkazy**|Vyhledá a zvýrazní všechny odkazy na vybraný typ. To zahrnuje elementy a atributy vybraného typu a typy odvozené z vybraného typu.|
|**Zobrazit všechny odvozené typy**|Najde a zvýrazní všechny typy, které jsou přímo a nepřímo odvozené z vybraného typu.|
|**Zobrazit všechny nadřazené prvky**|Zobrazit všechny nadřazené (základní) typy.|

## <a name="node-type-attribute"></a>Typ uzlu: atribut
Kromě možností globálního uzlu popsaných výše má kontextová nabídka pro uzly atributů následující možnosti:

|Možnost|Popis|
|-|-----------------|
|**Přejít na definici typu**|Pokud typ, který je použit pro atribut, je globální typ, přejde na definici typu vybraného atributu.|
|**Přejít k původnímu atributu**|Pro odkazy na atributy přejdete na skutečnou definici atributu.|
|**Zobrazit všechny odkazy**|U globálních atributů najde a zvýrazní všechny odkazy (další atributy, které mají `ref="selectedAttribute"` ) na vybraný atribut.|

## <a name="node-type-attribute-group"></a>Typ uzlu: skupina atributů
Kromě možností globálního uzlu popsaných výše má kontextová nabídka pro uzly skupin atributů následující možnosti:

|Možnost|Popis|
|-|-----------------|
|**Přejít k definici**|V případě odkazů přejdete na skutečnou definici atributu.|
|**Zobrazit všechny členy**|Vyhledá a zvýrazní všechny členy skupiny atributů.|
|**Zobrazit všechny odkazy**|Vyhledá a zvýrazní všechny odkazy (skupiny atributů, které mají `ref="selectedAttributeGroup"` ) na vybranou skupinu atributů.|

## <a name="node-type-named-group"></a>Typ uzlu: pojmenovaná skupina
Kromě možností globálních uzlů popsaných výše má kontextová nabídka pro pojmenované skupiny následující možnosti:

|Možnost|Popis|
|-|-----------------|
|**Přejít k definici**|V případě odkazů přejdete na skutečnou definici atributu.|
|**Zobrazit všechny členy**|Vyhledá a zvýrazní všechny členy pojmenované skupiny.|
|**Zobrazit všechny odkazy**|Vyhledá a zvýrazní všechny odkazy (skupiny, které mají `ref="selectedGroup"` ) na vybranou skupinu.|

## <a name="see-also"></a>Viz také

- [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)
- [Hledání sady schémat](../xml-tools/searching-the-schema-set.md)
