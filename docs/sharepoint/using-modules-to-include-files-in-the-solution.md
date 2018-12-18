---
title: Vložené soubory v řešení pomocí modulů | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0773d9c167a0a799b7d9bc8ddd2b52afc9bc6f2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120177"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Vložené soubory v řešení pomocí modulů
  Může nastat situace, kdy můžete chtít nasadit soubory na server SharePoint bez ohledu na jejich typ souboru, jako je například nové stránky předlohy. Chcete-li to provést, můžete použít *moduly* (Nezaměňovat s [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] code moduly). Moduly jsou kontejnery pro soubory v řešení služby SharePoint. Po nasazení řešení se soubory v modulu se zkopírují do zadané složky na serveru SharePoint.  
  
## <a name="module-items-and-elements"></a>Modul položky a elementy
 Vytvořit modul, přidejte ji do projektu ji v výběrem **přidat novou položku** dialogové okno. Potom upravte jeho *Elements.xml* souboru názvy souborů, které chcete nasadit, kde se nacházejí v systému, a kde mají být zkopírovány na server služby SharePoint.  
  
 Tady je příklad *Elements.xml* soubor pro modul:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Nově vytvořený moduly obsahují následující výchozí soubory:  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|*Elements.XML*|Soubor definice modulu.|  
|*Ukázka.txt*|Zástupný soubor, který slouží jako příklad souboru v modulu.|  
  
 *Elements.xml* soubor obsahuje následující prvky:  
  
|Název elementu|Popis|  
|------------------|-----------------|  
|Elementy|Obsahuje všechny prvky definované v modulu.|  
|Modul|Element modulu má jeden atribut, *název*, který určuje název modulu ve formátu `<Module Name="Module1">`.<br /><br /> Všimněte si, že pokud změníte název měněného modulu (nebo její *název složky* vlastnost), je nutné ručně aktualizovat název v elementu modulu.<br /><br /> Pokud podadresáři pro soubory, které zadáte v elementu modulu [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) automaticky vytvoří odpovídající adresářovou strukturu pro ně.|  
|Soubor|Element souboru má dva parametry *cesta* a *Url*.<br /><br /> -Path: Název a umístění souboru v řešení služby SharePoint. Formát je, `Path="Module1\Sample.txt"`.<br /><br /> -Adresa Url: Umístění, kde bude soubor nasazen na serveru SharePoint. Formát je, `Url="Module1/Sample.txt"`.<br /><br /> -Type: Volitelný atribut, který má dvě nastavení: *GhostableInLibrary* a *Ghostable*. Formát je, `Type="GhostableInLibrary"`. Určení *GhostableInLibrary* znamená přidá soubor do knihovny dokumentů ve službě SharePoint společně s položku seznamu, který může doprovázet soubor při jejím přidání do knihovny. Určení *Ghostable* způsobí, že soubor, který se má přidat do služby SharePoint mimo knihovnu dokumentů.|  
  
 Každý soubor, který chcete nasadit vyžaduje samostatné `<File>` element položku v *Elements.xml*.  
  
## <a name="see-also"></a>Viz také:
 [Postupy: zahrnutí souborů pomocí modulu](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [postupy: zřídit soubor](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [Vývoj řešení služby SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Vytvoření webové části pro službu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Zabalení a nasazení řešení služby SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
