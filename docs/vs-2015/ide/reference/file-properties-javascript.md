---
title: Soubor vlastností, JavaScript | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8db05d62bd1a8b1e1bf5fee6642810c654265c97
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909728"
---
# <a name="file-properties-javascript"></a>Vlastnosti souboru, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Vlastnosti souboru můžete použít k označení jaké akce systém projektu by měl provádět na souborech. Můžete třeba nastavit vlastnosti souboru k označení, zda má soubor přidat do balíčku jako soubor prostředků.  
  
 Můžete vybrat libovolný soubor v Průzkumníku řešení a pak zkontrolujte její vlastnosti v okně Vlastnosti. Soubory JavaScript obsahují čtyři vlastnosti: **kopírovat do výstupního adresáře**, **akce balíčku**, **název_souboru**, a **cesta k souboru**.  
  
## <a name="file-properties"></a>Vlastnosti souboru  
 Tato část popisuje vlastnosti, které jsou společné pro soubory jazyka JavaScript.  
  
### <a name="copy-to-output-directory-property"></a>Kopírovat do výstupního adresáře vlastnost  
 Tato vlastnost určuje podmínky, za kterých bude možné vybraný zdrojový soubor zkopírován do výstupního adresáře. Vyberte **nekopírovat** Pokud je soubor nikdy, které se mají zkopírovat do výstupního adresáře. Vyberte **vždy Kopírovat** je-li soubor vždy zkopírovány do výstupního adresáře. Vyberte **kopírovat, pokud je novější** Pokud je soubor, které se mají zkopírovat, pouze pokud je novější než stávající soubor se stejným názvem ve výstupním adresáři.  
  
### <a name="package-action"></a>Akce balíčku  
 **Akce balíčku** vlastnost indikuje, co Visual Studio dělá pomocí souboru při spuštění sestavení. **Balíček akce** může mít jednu z několika hodnot:  
  
- **Žádný** – soubor není zahrnutý v manifestu balíčku. Příkladem je textový soubor, který obsahuje dokumentaci, například soubor Readme.  
  
- **Obsahu** – soubor je zahrnutý v manifestu balíčku. Například toto nastavení je výchozí hodnota pro HTML, JS, CSS, obrázek, zvukový nebo video soubor.  
  
- **Manifest** – soubor není zahrnutý v manifestu balíčku. Místo toho soubor se používá pro vstup při generování manifestu balíčku. Toto je výchozí hodnota pro soubor package.appxmanifest.  
  
- **Prostředek** – soubor není zahrnutý v manifestu balíčku. Obsah souboru místo toho jsou indexovány v balíček prostředků indexu (PRI), která přejdou do manifestu balíčku. To se obvykle používá pro soubory prostředků.  
  
  Výchozí hodnota pro **akce balíčku** závisí na příponu souboru, který přidáte do řešení.  
  
### <a name="file-name-property"></a>Vlastnost název souboru  
 Zobrazuje název souboru jako hodnota určená pouze pro čtení. Pokud chcete přejmenovat soubor, klikněte pravým tlačítkem v Průzkumníku řešení a vyberte **přejmenovat**.  
  
### <a name="full-path-property"></a>Úplná cesta k vlastnosti  
 Zobrazí úplnou cestu k souboru jako hodnota určená pouze pro čtení. Chcete-li změnit cestu k souboru, můžete a přetahování souborů v Průzkumníku řešení.  
  
## <a name="reference-file-properties"></a>Vlastnosti odkazu na soubor  
 Tato část popisuje vlastnosti společné pro soubory, které odkazuje [!INCLUDE[win8_app_js](../../includes/win8-app-js-md.md)]. Když vyberete odkaz jako soubor .winmd, odkaz na sadu SDK, odkaz typu projekt projekt nebo odkaz na sestavení v Průzkumníku řešení, ostatní vlastnosti se může zobrazit v okně Vlastnosti podle typu souboru.  
  
### <a name="culture"></a>Jazyková verze  
 Zobrazí jazyk přidružený k odkazu.  
  
### <a name="file-type"></a>Typ souboru  
 Zobrazí typ souboru odkazu.  
  
### <a name="file-version"></a>Verze souboru  
 Zobrazí verzi souboru odkazu.  
  
### <a name="identity"></a>Identita  
 Zobrazí identitu, odkazu, který se používá v projektu, který je uložený v souboru projektu.  
  
### <a name="package"></a>Balíček  
 Zobrazí název manifestu balíčku přidruženého odkazu.  
  
### <a name="resolved-path"></a>Vyhodnocená cesta  
 Zobrazuje cestu k odkazu, který se používá v projektu.  
  
### <a name="sdk-path"></a>Cestu k sadě SDK  
 Zobrazuje cestu k odkazovanému souboru sady SDK.  
  
### <a name="uri"></a>Identifikátor URI  
 Zobrazuje identifikátor URI, který musí být součástí projektu HTML nebo JavaScript soubory k zahrnutí souboru jako zdrojový soubor.  
  
### <a name="version"></a>Version  
 Zobrazí verze odkazu.  
  
## <a name="see-also"></a>Viz také  
 [NIB: Vlastnosti projektu (Visual Studio)](http://msdn.microsoft.com/en-us/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)



