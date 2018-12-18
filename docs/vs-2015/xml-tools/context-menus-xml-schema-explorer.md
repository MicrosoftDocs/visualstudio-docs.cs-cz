---
title: Kontextové nabídky (Průzkumník schémat XML) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 854ea473f2f606b28052b093978253372b4fec59
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294610"
---
# <a name="context-menus-xml-schema-explorer"></a>Kontextové nabídky (Průzkumník schémat XML)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Následující položky místní nabídky jsou používány k provádění specifické pro schéma vyhledávání a další operace.  
  
## <a name="node-type-schema-set"></a>Typ uzlu: Sadě schémat.  
 Následující tabulka popisuje možnosti, které jsou k dispozici pro schéma, nastavte uzel.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Zobrazit pravděpodobně kořenové prvky**|Vyhledá a zvýrazní všechny globální prvky, které nejsou odkazovány z globální prvky výjimkou sama sebe.|  
|**Zobrazit globální typy**|Vyhledá a zvýrazní všechny globální typy v sadě schémat.|  
|**Zobrazit globální prvky**|Vyhledá a zvýrazní všechny globální prvky v sadě schémat.|  
|**Okno Vlastnosti**|Otevře **vlastnosti** okna (pokud ještě není otevřený). Toto okno zobrazuje informace o uzlu.|  
  
## <a name="node-type-namespace"></a>Typ uzlu: Namespace  
 Následující tabulka popisuje možnosti, které jsou k dispozici pro uzel oboru názvů.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Zobrazit všechny příchozí odkazy**|Vyhledá a zvýrazní soubory, které importují vybraný obor názvů.|  
|**Zobrazit všechny odchozí odkazy**|Pro každý soubor ve vybraném oboru názvů, najde a zvýrazní následující:<br /><br /> -Všechny obory názvů odkazované v příkazy bez importu `schemaLocation` atribut.<br />-Všechny soubory v oborech názvů než vybraný ve stanoveném `schemaLocation` atribut v importu a #include.|  
|**Zobrazit globální typy**|Vyhledá a zvýrazní všechny globální typy ve vybraném oboru názvů.|  
|**Zobrazit globální prvky**|Vyhledá a zvýrazní všechny globální prvky ve vybraném oboru názvů.|  
|**Okno Vlastnosti**|Otevře **vlastnosti** okna (pokud ještě není otevřený). Toto okno zobrazuje informace o uzlu.|  
  
## <a name="node-type-file"></a>Typ uzlu: soubor  
 Následující tabulka popisuje možnosti, které jsou k dispozici pro uzel souboru.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Zobrazit všechny příchozí odkazy**|Vyhledá a zvýrazní všechny soubory, které určují, na vybraný soubor na `schemaLocation` atributů jejich zahrnutí a import příkazů.|  
|**Zobrazit všechny odchozí odkazy**|Najde a upozorňuje na následující:<br /><br /> -Import všechny obory názvů určen v oboru názvů atributů všechny příkazy, které nemají `schemaLocation` atribut.<br />-Všechny soubory v zadané `schemaLocation` všechny atributy import a #include.|  
|**Zobrazit globální typy**|Vyhledá a zvýrazní všechny globální typy v tomto souboru.|  
|**Zobrazit globální prvky**|Vyhledá a zvýrazní všechny globální prvky v tomto souboru.|  
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položky vybrané v Průzkumník schémat XML bude také vybrána v editoru XML.|  
|**Okno Vlastnosti**|Otevře **vlastnosti** okna (pokud ještě není otevřený). Toto okno zobrazuje informace o uzlu.|  
  
## <a name="all-global-node-types"></a>Všechny typy globální uzlu  
 Následující tabulka popisuje možnosti, které jsou k dispozici pro všechny globální uzly.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Zobrazit v zobrazení grafu**|Otevře se zobrazení grafu. Pokud vybraný uzel není v pracovním prostoru, přidá ho do pracovního prostoru a vybere uzel.|  
|**Zobrazit v zobrazení modelu obsahu**|Otevře se zobrazení modelu obsahu. Pokud vybraný uzel není v pracovním prostoru, přidá ho do pracovního prostoru a vybere uzel.|  
|**Zobrazit kód**|Otevře soubor, který obsahuje vybraný uzel v editoru XML. Položky vybrané v Průzkumník schémat XML bude také vybrána v editoru XML.|  
|**Okno Vlastnosti**|Otevře **vlastnosti** okna (pokud ještě není otevřený). Toto okno zobrazuje informace o uzlu.|  
  
## <a name="node-type-element"></a>Typ uzlu: Element  
 Kromě možností globální uzlu je popsáno výše kontextovou nabídku pro uzly element má následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přejít k definici typu**|Přejde do definice typu vybraného prvku. To se vztahuje, pokud je typ, který se používá pro element globálního typu.|  
|**Přejít na původní Element**|Pro element reference přejde na skutečnou definici elementu.|  
|**Zobrazit všechny odkazy**|Globální prvky, najde a zvýrazní všechny odkazy (elementy, které mají `ref="selectedElement"`) na vybraný prvek.|  
|**Zobrazit členy skupiny nahrazení**|Vedoucích Substituční skupina, najde a zvýrazní všechny elementy, které jsou členy skupiny nahrazení, který vybraný prvek je jejím členem. Ukazuje to přímé a nepřímé účastníky.|  
|**Zobrazit nahrazování skupinu vedoucích**|Pro globální prvky, které jsou členy skupiny nahrazení, najde a zvýrazní všechny přímou a nepřímou heads pro vybraný element, jako je následující:<br /><br /> -Substituční skupiny head na vybraný prvek.<br />-Substituční skupiny head na jeho element head.|  
|**Generovat ukázkový soubor XML**|K dispozici pouze pro globální prvky. Generuje ukázkový soubor XML pro prvek globální.|  
  
## <a name="node-type-global-types"></a>Typ uzlu: Globální typy  
 Kromě možností globální uzlu je popsáno výše obsahuje místní nabídku pro uzel typu globální následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Zobrazit základní typ**|Pokud je vybraný typ je odvozen od typu globální, přejde na základní typ vybraného typu.|  
|**Zobrazit všechny odkazy**|Vyhledá a zvýrazní všechny odkazy na vybraného typu. To zahrnuje elementy a atributy vybraného typu a typy odvozené od vybraného typu.|  
|**Zobrazit všechny odvozené typy**|Vyhledá a zvýrazní všechny typy, které jsou přímo i nepřímo odvozeny z vybraného typu.|  
|**Zobrazení všech nadřazených**|Zobrazit všechny typy nadřazené (základní).|  
  
## <a name="node-type-attribute"></a>Typ uzlu: atribut  
 Kromě možností globální uzlu je popsáno výše kontextovou nabídku pro uzlů atributů obsahuje následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přejít k definici typu**|Pokud je typ, který se používá pro atribut globálního typu, přejde do definice typu vybraného atributu.|  
|**Přejít na původní atribut**|Pro atribut odkazy přejde na skutečné definice atributu.|  
|**Zobrazit všechny odkazy**|Globální atributy, najde a zvýrazní všechny odkazy (jiné atributy, které mají `ref="selectedAttribute"`) pro vybraný atribut.|  
  
## <a name="node-type-attribute-group"></a>Typ uzlu: Skupina atributů  
 Kromě možností globální uzlu je popsáno výše obsahuje místní nabídku pro atribut skupiny uzlů následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přejít k definici**|Odkazy přejde na skutečné definice atributu.|  
|**Zobrazit všechny členy**|Vyhledá a zvýrazní všechny členy skupiny atributů.|  
|**Zobrazit všechny odkazy**|Vyhledá a zvýrazní všechny odkazy (atribut skupiny, které mají `ref="selectedAttributeGroup"`) ke skupině pro vybraný atribut.|  
  
## <a name="node-type-named-group"></a>Typ uzlu: Pojmenované skupiny  
 Kromě možností globální uzlu je popsáno výše obsahuje místní nabídku pro pojmenovanou skupinu uzlů následující možnosti:  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přejít k definici**|Odkazy přejde na skutečné definice atributu.|  
|**Zobrazit všechny členy**|Vyhledá a zvýrazní všechny členy pojmenované skupiny.|  
|**Zobrazit všechny odkazy**|Vyhledá a zvýrazní všechny odkazy (skupiny, které mají `ref="selectedGroup"`) do vybrané skupiny.|  
  
## <a name="see-also"></a>Viz také  
 [Průzkumník schémat XML](../xml-tools/xml-schema-explorer.md)   
 [Hledání v sadě schémat](../xml-tools/searching-the-schema-set.md)



