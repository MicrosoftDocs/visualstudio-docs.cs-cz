---
title: Společné položky projektu nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e36d5e50b15a5ede425715ec756f05ab8d014de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160413"
---
# <a name="common-msbuild-project-items"></a>Společné položky projektu nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V je [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] položka pojmenovaný odkaz na jeden nebo více souborů. Položky obsahují metadata, jako jsou názvy souborů, cesty a čísla verzí. Všechny typy projektů v aplikaci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] mají několik společných položek. Tyto položky jsou definovány v souboru Microsoft. Build. CommonTypes. xsd.  
  
## <a name="common-items"></a>Společné položky  
 Níže je seznam všech běžných položek projektu.  
  
### <a name="reference"></a>Referenční informace  
 Představuje odkaz sestavení (spravovaného) v projektu.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|Cestu|Volitelný řetězec. Relativní nebo absolutní cesta k sestavení|  
|Název|Volitelný řetězec. Zobrazovaný název sestavení, například "System. Windows. Forms."|  
|Fusion|Volitelný řetězec. Určuje jednoduchý nebo silný název fúze pro položku.<br /><br /> Pokud je tento atribut přítomen, může ušetřit čas, protože soubor sestavení není nutné otevřít, aby získal název fúze.|  
|SpecificVersion|Volitelná logická hodnota. Určuje, zda má být odkazována pouze verze v názvu fúze.|  
|Aliasy|Volitelný řetězec. Všechny aliasy pro referenci|  
|Soukromá|Volitelná logická hodnota. Určuje, zda má být odkaz zkopírován do výstupní složky. Tento atribut odpovídá vlastnosti **Copy Local** odkazu, který je v integrovaném vývojovém prostředí sady Visual Studio.|  
  
### <a name="comreference"></a>COMReference  
 Představuje odkaz na komponentu modelu COM (nespravovaný) v projektu.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|Název|Volitelný řetězec. Zobrazovaný název součásti.|  
|Identifikátor GUID|Volitelný řetězec. Identifikátor GUID pro komponentu ve formuláři {12345678-1234-1234-1234-1234567891234} .|  
|VersionMajor|Volitelný řetězec. Hlavní část čísla verze součásti. Například "5", pokud je číslo úplné verze "5,46".|  
|VersionMinor|Volitelný řetězec. Vedlejší část čísla verze součásti. Například "46", pokud je číslo úplné verze "5,46".|  
|LCID|Volitelný řetězec. LocaleID pro komponentu|  
|WrapperTool|Volitelný řetězec. Název nástroje obálky, který se používá pro komponentu, například "Tlbimp".|  
|Isolated|Volitelná logická hodnota. Určuje, zda je komponenta komponentou bez registrace.|  
  
### <a name="comfilereference"></a>COMFileReference  
 Představuje seznam knihoven typů, které jsou předávány do cíle ResolvedComreference.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|WrapperTool|Volitelný řetězec. Název nástroje obálky, který se používá pro komponentu, například "Tlbimp".|  
  
### <a name="nativereference"></a>NativeReference  
 Představuje nativní soubor manifestu nebo odkaz na takový soubor.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|Název|Povinný řetězec. Základní název souboru manifestu.|  
|Cestu|Povinný řetězec. Relativní cesta k souboru manifestu.|  
  
### <a name="projectreference"></a>ProjectReference  
 Představuje odkaz na jiný projekt.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|Název|Volitelný řetězec. Zobrazovaný název odkazu|  
|Project|Volitelný řetězec. Identifikátor GUID odkazu ve formuláři {12345678-1234-1234-1234-1234567891234} .|  
|Balíček|Volitelný řetězec. Cesta k souboru projektu, na který se odkazuje|  
  
### <a name="compile"></a>Sestavení  
 Představuje zdrojové soubory pro kompilátor.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|DependentUpon|Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje.|  
|AutoGen|Volitelná logická hodnota. Označuje, zda byl soubor generován pro projekt pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE).|  
|Odkaz|Volitelný řetězec. Cesta k zápisu, která se má zobrazit, pokud je soubor fyzicky umístěný mimo vliv souboru projektu.|  
|Viditelné|Volitelná logická hodnota. Určuje, zda se má soubor zobrazit v **Průzkumník řešení** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest|  
  
### <a name="embeddedresource"></a>EmbeddedResource  
 Představuje prostředky, které mají být vloženy do generovaného sestavení.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|DependentUpon|Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje.|  
|Generátor|Povinný řetězec. Název jakéhokoli generátoru souborů, který je spuštěn na této položce.|  
|LastGenOutput|Povinný řetězec. Název souboru, který byl vytvořen generátorem souborů, který u této položky běžel.|  
|CustomToolNamespace|Povinný řetězec. Obor názvů, ve kterém má každý generátor souborů, který běží na této položce, vytvořit kód.|  
|Odkaz|Volitelný řetězec. Cesta k zápisu se zobrazí, pokud je soubor fyzicky umístěný mimo vliv projektu.|  
|Viditelné|Volitelná logická hodnota. Určuje, zda se má soubor zobrazit v **Průzkumník řešení** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest|  
|Logický operátor|Povinný řetězec. Logický název vloženého prostředku.|  
  
### <a name="content"></a>Content  
 Představuje soubory, které nejsou zkompilovány do projektu, ale mohou být vloženy nebo publikovány společně s ní.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|DependentUpon|Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje.|  
|Generátor|Povinný řetězec. Název jakéhokoli generátoru souborů, který se na této položce spouští.|  
|LastGenOutput|Povinný řetězec. Název souboru, který byl vytvořen generátorem souborů spuštěným u této položky.|  
|CustomToolNamespace|Povinný řetězec. Obor názvů, ve kterém má každý generátor souborů, který běží na této položce, vytvořit kód.|  
|Odkaz|Volitelná logická hodnota. Určuje, zda se má soubor zobrazit v **Průzkumník řešení** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|PublishState|Povinný řetězec. Stav publikování obsahu, a to buď:<br /><br /> – Výchozí<br />– Zahrnuto<br />– Vyloučené<br />– Datový datový<br />– Předpoklad|  
|Sestavení|Volitelná logická hodnota. Určuje, zda je soubor sestavením.|  
|Viditelné|Volitelná logická hodnota. Určuje, zda se má soubor zobrazit v **Průzkumník řešení** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest|  
  
### <a name="none"></a>Žádné  
 Představuje soubory, které by neměly mít žádné role v procesu sestavení.  
  
|Název položky|Popis|  
|---------------|-----------------|  
|DependentUpon|Volitelný řetězec. Určuje soubor, na kterém je tento soubor závislý, aby se správně zkompiluje.|  
|Generátor|Povinný řetězec. Název jakéhokoli generátoru souborů, který je spuštěn na této položce.|  
|LastGenOutput|Povinný řetězec. Název souboru, který byl vytvořen generátorem souborů, který u této položky běžel.|  
|CustomToolNamespace|Povinný řetězec. Obor názvů, ve kterém má každý generátor souborů, který běží na této položce, vytvořit kód.|  
|Odkaz|Volitelný řetězec. Cesta k zápisu, která se má zobrazit, pokud je soubor fyzicky umístěný mimo vliv projektu.|  
|Viditelné|Volitelná logická hodnota. Určuje, zda se má soubor zobrazit v **Průzkumník řešení** v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|Volitelný řetězec. Určuje, zda se má soubor zkopírovat do výstupního adresáře. Hodnoty jsou:<br /><br /> 1. nikdy<br />2. vždycky<br />3. PreserveNewest|  
  
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest  
 Představuje manifest základní aplikace pro sestavení a obsahuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] informace o zabezpečení nasazení.  
  
### <a name="codeanalysisimport"></a>CodeAnalysisImport  
 Představuje projekt FxCop, který se má importovat.  
  
### <a name="import"></a>Import  
 Představuje sestavení, jejichž obory názvů by měly být importovány [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilátorem.  
  
## <a name="see-also"></a>Viz také  
 [Obecné vlastnosti projektu nástroje MSBuild](../msbuild/common-msbuild-project-properties.md)
