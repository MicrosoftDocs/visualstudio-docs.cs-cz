---
title: Zahrnutí souborů do řešení pomocí modulů | Microsoft Docs
description: Použijte moduly nebo kontejnery pro soubory v řešení služby SharePoint pro nasazení souborů na server SharePoint bez ohledu na jejich typ souboru (například stránky předlohy).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aa0d6fe1855a1d60a0e1293e8422791f8148bd04
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442518"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Zahrnutí souborů do řešení pomocí modulů
  Mohou nastat situace, kdy můžete chtít nasadit soubory na server SharePoint bez ohledu na jejich typ souboru, například na nové stránky předlohy. K tomu můžete použít *moduly* (Nepleťe se s [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] moduly kódu). Moduly jsou kontejnery pro soubory v řešení služby SharePoint. Po nasazení řešení se soubory v modulu zkopírují do zadaných složek na SharePointovém serveru.

## <a name="module-items-and-elements"></a>Položky modulu a prvky
 Chcete-li vytvořit modul, přidejte jej do projektu výběrem v dialogovém okně **Přidat novou položku** . Pak upravte svůj soubor *Elements.xml* tak, aby obsahoval názvy souborů, které chcete nasadit, kde jsou umístěny v systému a kde by měly být zkopírovány na server služby SharePoint.

 Tady je příklad souboru *Elements.xml* pro modul:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">
    <Module Name="Module1">
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />
    </Module>
</Elements>

```

 Nově vytvořené moduly obsahují následující výchozí soubory:

|Název souboru|Popis|
|---------------|-----------------|
|*Elements.xml*|Definiční soubor pro modul|
|*Sample.txt*|Zástupný soubor, který slouží jako příklad souboru v modulu.|

 *Elements.xml* soubor obsahuje následující prvky:

|Název prvku|Popis|
|------------------|-----------------|
|Elementy|Obsahuje všechny prvky, které jsou definovány v modulu.|
|Modul|Element Module má jeden atribut *Name*, který určuje název modulu ve formátu `<Module Name="Module1">` .<br /><br /> Všimněte si, že pokud změníte název modulu (nebo jeho vlastnosti *názvu složky* ), je nutné ručně aktualizovat název v elementu Module.<br /><br /> Pokud zadáte podadresář pro soubory v elementu modulu, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) automaticky vytvoří pro ně stejnou strukturu adresářů.|
|Soubor|Element File má dva parametry, *cesta* a *adresu URL*.<br /><br /> -Path: název a umístění souboru v řešení služby SharePoint. Formát je, `Path="Module1\Sample.txt"` .<br /><br /> -URL: umístění, kam se soubor nasadí na SharePointovém serveru. Formát je, `Url="Module1/Sample.txt"` .<br /><br /> -Type: volitelný atribut, který má dvě nastavení: *GhostableInLibrary* a *Ghost*. Formát je, `Type="GhostableInLibrary"` . Při zadání *GhostableInLibrary* znamená, že se soubor přidá do knihovny dokumentů ve službě SharePoint společně s položkou seznamu, která bude doprovázet soubor při jeho přidání do knihovny. Zadáte-li nemožné *duplikování* , soubor se přidá do SharePointu mimo knihovnu dokumentů.|

 Každý soubor, který chcete nasadit, vyžaduje samostatnou `<File>` položku elementu v *Elements.xml*.

## <a name="see-also"></a>Viz také
- [Postupy: zahrnutí souborů pomocí modulu](../sharepoint/how-to-include-files-by-using-a-module.md)
- [Postupy: zřízení souboru](/previous-versions/office/developer/sharepoint-2010/ms441170(v=office.14))
- [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Vytváření webových částí pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
