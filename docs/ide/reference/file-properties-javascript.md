---
title: Vlastnosti souboru, JavaScript
ms.date: 06/21/2017
ms.technology: vs-javascript
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b27f103b2431914efbd22c119e11221b5814dae4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926238"
---
# <a name="file-properties-javascript"></a>Vlastnosti souboru, JavaScript

Pomocí vlastností souboru můžete určit, jaké akce by měl systém projektu provádět se soubory. Můžete například nastavit vlastnosti souboru, které označují, zda má být soubor přidán do balíčku jako soubor prostředků.

V Průzkumníku řešení můžete vybrat libovolný soubor a potom zkontrolovat jeho vlastnosti v okně Vlastnosti. Soubory JavaScriptu mají čtyři vlastnosti: **Kopírovat do výstupního adresáře**, **Akci balíčku**, **Název souboru**a **Cesta k souboru**.

## <a name="file-properties"></a>Vlastnosti souboru
Tato část popisuje vlastnosti společné souborům JavaScript.

### <a name="copy-to-output-directory-property"></a>Kopírovat do vlastnosti výstupního adresáře
Tato vlastnost určuje podmínky, za kterých bude vybraný zdrojový soubor zkopírován do výstupního adresáře. Vyberte **Nekopírovat,** pokud se soubor nikdy nezkopíruje do výstupního adresáře. Pokud se má soubor vždy kopírovat do výstupního adresáře, vyberte vždy možnost **Kopírovat.** Vyberte **Kopírovat, pokud novější,** pokud má být soubor zkopírován pouze v případě, že je novější než existující soubor se stejným názvem ve výstupním adresáři.

### <a name="package-action"></a>Akce balíčku
Vlastnost **Akce balíčku** označuje, co visual studio dělá se souborem při spuštění sestavení. **Akce balíčku** může mít jednu z několika hodnot:

- **Žádný** - Soubor není součástí manifestu balíčku. Příkladem je textový soubor, který obsahuje dokumentaci, například soubor Readme.

- **Content** - Soubor je součástí manifestu balíčku. Toto nastavení je například výchozí hodnotou souboru HTM, JS, CSS, image, zvuku nebo videa.

- **Manifest** - Soubor není součástí manifestu balíčku. Místo toho soubor se používá pro vstup při generování manifestu balíčku. Toto je výchozí hodnota pro soubor package.appxmanifest.

- **Prostředek** - Soubor není součástí manifestu balíčku. Místo toho obsah souboru jsou indexovány v indexu prostředků balíčku (PRI), který přejde do manifestu balíčku. Obvykle se používá pro soubory prostředků.

Výchozí hodnota akce **balíčku** závisí na příponě souboru, který přidáte do řešení.

### <a name="file-name-property"></a>Vlastnost Název souboru
Zobrazí název souboru jako hodnotu jen pro čtení. Chcete-li soubor přejmenovat, musíte klepnout pravým tlačítkem myši v Průzkumníku řešení a vybrat **možnost Přejmenovat**.

### <a name="full-path-property"></a>Úplná vlastnost cesty
Zobrazí úplnou cestu k souboru jako hodnotu jen pro čtení. Chcete-li změnit cestu k souboru, můžete soubor přetáhnout v Průzkumníku řešení.

## <a name="reference-file-properties"></a>Vlastnosti referenčního souboru
Tato část popisuje vlastnosti společné pro soubory odkazované z aplikace UPW vytvořené pomocí JavaScriptu. Když vyberete odkaz, například soubor .winmd, odkaz sady SDK, odkaz na projekt na projekt nebo odkaz na sestavení v Průzkumníku řešení, mohou se v okně Vlastnosti zobrazit další vlastnosti podle typu souboru.

### <a name="culture"></a>Culture
Zobrazí jazyk přidružený k odkazu.

### <a name="file-type"></a>Typ souboru
Zobrazí typ souboru odkazu.

### <a name="file-version"></a>Verze souboru
Zobrazí verzi odkazu pro soubor.

### <a name="identity"></a>Identita
Zobrazí identitu odkazu, který se používá v projektu, který je uložen v souboru projektu.

### <a name="package"></a>Balíček
Zobrazí název manifestu balíčku přidruženého k odkazu.

### <a name="resolved-path"></a>Přeložená cesta
Zobrazí cestu k odkazu, který se používá v projektu.

### <a name="sdk-path"></a>Cesta sady SDK
Zobrazí cestu k odkazovanému souboru sady SDK.

### <a name="uri"></a>Uri
Zobrazí identifikátor URI, který musí být zahrnut do souborů HTML nebo JavaScript u projektu, aby byl soubor zahrnut jako zdrojový soubor.

### <a name="version"></a>Version
Zobrazí verzi odkazu.

## <a name="see-also"></a>Viz také

- [Správa vlastností projektů a řešení](../../ide/managing-project-and-solution-properties.md)