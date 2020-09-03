---
title: Vlastnosti souboru, JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 719a956558141684c7d755aafb6929f4368482f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657726"
---
# <a name="file-properties-javascript"></a>Vlastnosti souboru, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí vlastností souboru můžete určit, jaké akce má projektový systém provádět na souborech. Můžete například nastavit vlastnosti souboru a určit, jestli se má soubor přidat do balíčku jako soubor prostředků.

 Můžete vybrat libovolný soubor v Průzkumník řešení a potom prostudovat jeho vlastnosti v okno Vlastnosti. Soubory JavaScriptu mají čtyři vlastnosti: **Kopírovat do výstupního adresáře**, **Akce balíčku**, **název souboru**a **cestu k souboru**.

## <a name="file-properties"></a>Vlastnosti souboru
 Tato část popisuje vlastnosti společné pro soubory jazyka JavaScript.

### <a name="copy-to-output-directory-property"></a>Vlastnost kopírovat do výstupního adresáře
 Tato vlastnost určuje podmínky, za kterých se vybraný zdrojový soubor zkopíruje do výstupního adresáře. Pokud se soubor nikdy nekopíruje do výstupního adresáře, vyberte **Nekopírovat** . Vyberte možnost **Kopírovat vždy** , pokud je soubor vždy zkopírován do výstupního adresáře. Vyberte možnost **Kopírovat, pokud je novější** , pokud má být soubor zkopírován pouze v případě, že je novější než existující soubor se stejným názvem ve výstupním adresáři.

### <a name="package-action"></a>Akce balíčku
 Vlastnost **Akce balíčku** označuje, co sada Visual Studio obsahuje soubor při spuštění sestavení. **Akce balíčku** může mít jednu z několika hodnot:

- **Žádné** – soubor není zahrnutý v manifestu balíčku. Příkladem je textový soubor, který obsahuje dokumentaci, například soubor Readme.

- **Obsah** – soubor je součástí manifestu balíčku. Toto nastavení je například výchozí hodnota pro soubor. htm,. js,. CSS, obrázek, zvuk nebo videosoubor.

- **Manifest** – soubor není zahrnutý v manifestu balíčku. Místo toho se soubor při generování manifestu balíčku používá pro vstup. Toto je výchozí hodnota pro soubor Package. appxmanifest.

- **Prostředek** – soubor není zahrnutý v manifestu balíčku. Místo toho je obsah souboru indexován v indexu prostředků balíčku (PRI), který je součástí manifestu balíčku. Obvykle se používá pro soubory prostředků.

  Výchozí hodnota pro **akci balíčku** závisí na příponě souboru, který do řešení přidáte.

### <a name="file-name-property"></a>Vlastnost názvu souboru
 Zobrazí název souboru jako hodnotu určenou jen pro čtení. Chcete-li přejmenovat soubor, je nutné kliknout pravým tlačítkem myši na Průzkumník řešení a vybrat možnost **Přejmenovat**.

### <a name="full-path-property"></a>Vlastnost úplné cesty
 Zobrazí úplnou cestu k souboru jako hodnotu určenou jen pro čtení. Pokud chcete změnit cestu k souboru, můžete ho přetáhnout v Průzkumník řešení.

## <a name="reference-file-properties"></a>Vlastnosti referenčního souboru
 Tato část popisuje obecné vlastnosti souborů, na které odkazuje [!INCLUDE[win8_app_js](../../includes/win8-app-js-md.md)] . Když vyberete odkaz, jako je soubor. winmd, odkaz na sadu SDK, odkaz na projekt na projekt nebo odkaz na sestavení v Průzkumník řešení, další vlastnosti se mohou v okno Vlastnosti zobrazit podle typu souboru.

### <a name="culture"></a>Kultura
 Zobrazuje jazyk přidružený k odkazu.

### <a name="file-type"></a>Typ souboru
 Zobrazí typ souboru odkazu.

### <a name="file-version"></a>Verze souboru
 Zobrazuje verzi souboru odkazu.

### <a name="identity"></a>Identita
 Zobrazuje identitu odkazu, který je použit v projektu, který je uložen v souboru projektu.

### <a name="package"></a>Balíček
 Zobrazuje název manifestu balíčku přidruženého k odkazu.

### <a name="resolved-path"></a>Přeložená cesta
 Zobrazuje cestu k odkazu, který se používá v projektu.

### <a name="sdk-path"></a>Cesta k sadě SDK
 Zobrazí cestu k odkazovanému souboru sady SDK.

### <a name="uri"></a>Identifikátor URI
 Zobrazuje identifikátor URI, který musí být součástí souborů HTML nebo JavaScript projektu pro zahrnutí souboru jako zdrojového souboru.

### <a name="version"></a>Verze
 Zobrazuje verzi odkazu.

## <a name="see-also"></a>Viz také
 [NIB: vlastnosti projektu (Visual Studio)](https://msdn.microsoft.com/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)
