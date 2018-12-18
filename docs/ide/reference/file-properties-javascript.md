---
title: Vlastnosti souboru, JavaScript
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db9809c48b9226e05b7617c860af524b1ac6daf6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947921"
---
# <a name="file-properties-javascript"></a>Vlastnosti souboru, JavaScript
Vlastnosti souboru můžete akcí systému projektu proveďte na soubory. Například můžete nastavit vlastnosti souboru k označení, zda soubor musí být přidaní do balíčku jako soubor prostředků.

 Můžete vybrat libovolný soubor v Průzkumníku řešení a pak zkontrolujte jeho vlastnosti v okně Vlastnosti. Soubory JavaScript mít čtyři vlastnosti: **kopírovat do výstupního adresáře**, **akce balíčku**, **název souboru**, a **cesta k souboru**.

## <a name="file-properties"></a>Vlastnosti souboru
 Tato část popisuje vlastnosti, které jsou společné pro soubory jazyka JavaScript.

### <a name="copy-to-output-directory-property"></a>Kopírovat do výstupního adresáře vlastnost
 Tato vlastnost určuje podmínky, za kterých soubor vybraný zdroj bude zkopírován do výstupního adresáře. Vyberte **nekopírovat** Pokud je soubor nikdy mají být zkopírovány do výstupního adresáře. Vyberte **vždy Kopírovat** Pokud je soubor vždy zkopírovány do výstupního adresáře. Vyberte **kopírovat, pokud je novější** Pokud je soubor zkopírovat jenom v případě, že je novější než existující soubor se stejným názvem v výstupnímu adresáři.

### <a name="package-action"></a>Akce balíčku
 **Akce balíčku** vlastnost určuje, co Visual Studio se souborem při sestavení. **Akce balíčku** může mít jednu z několika hodnot:

-   **Žádný** -soubor není zahrnutý v manifest balíčku. Příkladem je textový soubor, který obsahuje dokumentaci, jako je soubor Readme.

-   **Obsahu** – soubor je zahrnuta v manifest balíčku. Například toto nastavení je výchozí hodnota pro .htm, JS, .css, image, zvuk nebo video souboru.

-   **Manifest** -soubor není zahrnutý v manifest balíčku. Místo toho soubor se používá pro vstup při generování manifestu balíčku. Toto je výchozí hodnota pro soubor package.appxmanifest.

-   **Prostředek** -soubor není zahrnutý v manifest balíčku. Obsah souboru místo toho jsou uloženy v balíček prostředků indexu (PRI), klient se přepne do manifestu balíčku. Se obvykle používá pro soubory prostředků.

Výchozí hodnota pro **akce balíčku** závisí na příponě souboru, který přidáte do řešení.

### <a name="file-name-property"></a>Vlastnost název souboru
 Zobrazuje název souboru, jako hodnotu jen pro čtení. Pokud chcete přejmenovat soubor, musí v Průzkumníku řešení klikněte pravým tlačítkem a vyberte **přejmenovat**.

### <a name="full-path-property"></a>Úplná cesta vlastnost
 Úplná cesta k souboru se zobrazí jako hodnotu jen pro čtení. Chcete-li změnit cestu k souboru, můžete přetahování myší soubor v Průzkumníku řešení.

## <a name="reference-file-properties"></a>Vlastnosti souboru odkazu
 Tato část popisuje vlastnosti, které jsou společné pro soubory na něj odkazovat z aplikace pro UPW vytvořené pomocí jazyka JavaScript. Když vyberete odkaz například soubor .winmd, odkaz na sadu SDK, odkaz na projekt na projekt nebo odkaz na sestavení v Průzkumníku řešení, ostatní vlastnosti se může zobrazovat v okně Vlastnosti podle typu souboru.

### <a name="culture"></a>Jazyková verze
 Zobrazí jazyk přidružené k odkazu.

### <a name="file-type"></a>Typ souboru
 Zobrazí soubor typu odkaz.

### <a name="file-version"></a>Verze souboru
 Zobrazí verzi souboru odkazu.

### <a name="identity"></a>Identita
 Zobrazí identitu odkaz, který se používá v projektu, který je uložený v souboru projektu.

### <a name="package"></a>Balíček
 Zobrazuje název manifestu balíčku přidružené k odkazu.

### <a name="resolved-path"></a>Přeložená cesta
 Zobrazuje cestu k odkazu, který se používá v projektu.

### <a name="sdk-path"></a>Cesta k sadě SDK
 Zobrazuje cestu k souboru odkazované sady SDK.

### <a name="uri"></a>identifikátor URI
 Zobrazuje identifikátor URI, který musí být součástí souborů HTML nebo JavaScriptu projektu zahrnout soubor jako zdrojový soubor.

### <a name="version"></a>Version
 Zobrazí verzi odkaz.

## <a name="see-also"></a>Viz také

- [Správa vlastností projektů a řešení](../../ide/managing-project-and-solution-properties.md)