---
title: Publikování rozšíření pomocí příkazového řádku
description: Naučte se používat příkazový řádek k publikování rozšíření Visual Studio Marketplace, které vývojářům umožňuje vyhledat nová a aktualizovaná rozšíření.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3548c9a206e874848756944fb48d447c34e28cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078367"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Návod: publikování rozšíření sady Visual Studio prostřednictvím příkazového řádku

V tomto návodu se dozvíte, jak publikovat rozšíření sady Visual Studio na Visual Studio Marketplace pomocí příkazového řádku. Když přidáte rozšíření na web Marketplace, můžou vývojáři použít dialog [**rozšíření a aktualizace**](../ide/finding-and-using-visual-studio-extensions.md) k vyhledání nových a aktualizovaných rozšíření.

VsixPublisher.exe je nástroj příkazového řádku pro publikování rozšíření sady Visual Studio na webu Marketplace. K němu se dá dostat z \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe $ {VSInstallDir}. K dispozici jsou příkazy tohoto nástroje: **Publish**, **createPublisher**, **deletePublisher**, **deleteExtension**, **Login**, **logout**.

## <a name="commands"></a>Příkazy

### <a name="publish"></a>publish

Publikuje rozšíření na webu Marketplace. Příponou může být VSIX, soubor exe/MSI nebo odkaz. Pokud rozšíření už existuje se stejnou verzí, toto rozšíření se přepíše. Pokud rozšíření ještě neexistuje, vytvoří se nové rozšíření.

|Možnosti příkazu |Description |
|---------|---------|
|datová část (povinné) | Buď cestu k datové části, která se má publikovat, nebo odkaz, který se má použít, jako adresa URL pro další informace. |
|publishManifest (povinné) | Cesta k souboru manifestu publikování, který se má použít |
|ignoreWarnings | Seznam upozornění, která se mají ignorovat při publikování rozšíření Tato upozornění se při publikování rozšíření zobrazují jako zprávy z příkazového řádku. (například "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Osobní přístupový token (PAT), který se používá k ověření vydavatele. Pokud není zadaný, získá se od přihlášených uživatelů. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Vytvoří vydavatele na webu Marketplace. Také zaznamená vydavatele do počítače pro budoucí akce (například odstranění nebo publikování rozšíření).

|Možnosti příkazu |Description |
|---------|---------|
|DisplayName (povinné) | Zobrazovaný název vydavatele |
|Vydavatel (povinné) | Název vydavatele (například identifikátor). |
|personalAccessToken (povinné) | Osobní přístupový token, který se používá k ověření vydavatele. |
|shortDescription | Krátký popis vydavatele (nejedná se o soubor). |
|longDescription | Dlouhý popis vydavatele (nejedná se o soubor). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Odstraní vydavatele na webu Marketplace.

|Možnosti příkazu |Description |
|---------|---------|
|Vydavatel (povinné) | Název vydavatele (například identifikátor). |
|personalAccessToken (povinné) | Osobní přístupový token, který se používá k ověření vydavatele. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Odstraní rozšíření z webu Marketplace.

|Možnosti příkazu |Description |
|---------|---------|
|Přípona (povinné) | Název rozšíření, které se má odstranit |
|Vydavatel (povinné) | Název vydavatele (například identifikátor). |
|personalAccessToken | Osobní přístupový token, který se používá k ověření vydavatele. Pokud není zadaný, získá se od přihlášených uživatelů. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>přihlášení

Zaznamená vydavatele do počítače.

|Možnosti příkazu |Description |
|---------|---------|
|personalAccessToken (povinné | Osobní přístupový token, který se používá k ověření vydavatele. |
|Vydavatel (povinné) | Název vydavatele (například identifikátor). |
|Přepsat | Určuje, že by měl být stávající Vydavatel přepsán novým tokenem osobní přístup. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Zaznamená vydavatele z počítače.

|Možnosti příkazu |Description |
|---------|---------|
|Vydavatel (povinné) | Název vydavatele (například identifikátor). |
|ignoreMissingPublisher | Určuje, že by nástroj neměl být v případě, že zadaný Vydavatel ještě není přihlášený, nechybí. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>soubor publishManifest

Příkaz **publikovat** používá soubor publishManifest. Představuje všechna metadata o rozšíření, které musí Marketplace znát. Pokud je rozšíření nahrává z rozšíření VSIX, vlastnost identity musí mít pouze sadu "Internal". Důvodem je, že zbývající vlastnosti identity mohou být vygenerovány ze souboru vsixmanifest. Pokud je přípona MSI/exe nebo rozšíření odkazu, musí uživatel zadat požadovaná pole ve vlastnosti identity. Zbytek manifestu obsahuje informace specifické pro web Marketplace (například kategorie, zda je povoleno Q&A, atd.).

Ukázka souboru publishManifest rozšíření VSIX:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

Ukázka souborů MSI/EXE nebo propojení souboru publishManifest:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Soubory assetů

Soubory prostředků se dají zadat pro vkládání položek, jako jsou obrázky v souboru Readme. Například pokud má rozšíření následující dokument "Přehled" Markdownu:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Aby bylo možné v předchozím příkladu vyřešit "image/testlogo.png", může uživatel zadat "assetFiles" v manifestu publikování, jak je znázorněno níže:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Návod k publikování

### <a name="prerequisites"></a>Požadavky

Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Vytvoření rozšíření pro Visual Studio

V tomto případě použijeme výchozí rozšíření VSPackage, ale stejný postup je platný pro všechny typy rozšíření.

1. Vytvořte VSPackage v jazyce C# s názvem "TestPublish", který obsahuje příkaz nabídky. Další informace najdete v tématu [Vytvoření prvního rozšíření: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Zabalení rozšíření

1. Aktualizujte rozšíření vsixmanifest o správné informace o názvu produktu, autorovi a verzi.

   ![aktualizovat rozšíření vsixmanifest](media/update-extension-vsixmanifest.png)

2. Sestavte rozšíření v režimu **vydání** . Nyní bude rozšíření zabaleno jako VSIX ve složce \bin\Release.

3. Pokud chcete ověřit instalaci, můžete dvakrát kliknout na VSIX.

### <a name="test-the-extension"></a>Test rozšíření

 Než rozšíříte rozšíření, sestavíte a otestujete, abyste se ujistili, že je správně nainstalován v experimentální instanci aplikace Visual Studio.

1. V aplikaci Visual Studio spusťte ladění. pro otevření experimentální instance sady Visual Studio.

2. V experimentální instanci přejděte do nabídky **nástroje** a klikněte na **rozšíření a aktualizace...**. Rozšíření TestPublish by se mělo zobrazit v prostředním podokně a povolit.

3. V nabídce **nástroje** se ujistěte, že se zobrazí příkaz test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publikování rozšíření na webu Marketplace prostřednictvím příkazového řádku

1. Ujistěte se, že máte vytvořenou verzi pro vydání rozšíření a že je aktuální.

2. Ujistěte se, že jste vytvořili publishmanifest.jsa overview.md soubory.

3. Otevřete příkazový řádek a přejděte do adresáře $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Chcete-li vytvořit nového vydavatele, použijte následující příkaz:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Po úspěšném vytvoření vydavatele se zobrazí následující zpráva příkazového řádku:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Nový Vydavatel, který jste vytvořili, můžete ověřit tak, že přejdete na [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Chcete-li publikovat nové rozšíření, použijte následující příkaz:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Po úspěšném vytvoření vydavatele se zobrazí následující zpráva příkazového řádku:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Nové rozšíření, které jste publikovali, můžete ověřit tak, že přejdete na [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Nainstalovat rozšíření z Visual Studio Marketplace

Teď, když je rozšíření publikované, nainstalujte ho v aplikaci Visual Studio a otestujte tam.

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace...**.

2. Klikněte na **online** a vyhledejte TestPublish.

3. Klikněte na **Stáhnout**. Rozšíření bude pak naplánováno na instalaci.

4. Chcete-li dokončit instalaci, zavřete všechny instance aplikace Visual Studio.

## <a name="remove-the-extension"></a>Odebrání rozšíření

Rozšíření můžete odebrat z Visual Studio Marketplace a z počítače.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Odebrání rozšíření z webu Marketplace prostřednictvím příkazového řádku

1. Pokud chcete odebrat rozšíření, použijte následující příkaz:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Po úspěšném odstranění rozšíření se zobrazí následující zpráva příkazového řádku:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Odebrání rozšíření z počítače

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace**.

2. Vyberte "MyVsixExtension" a pak klikněte na **odinstalovat**. Rozšíření bude pak naplánováno pro odinstalaci.

3. Chcete-li dokončit odinstalaci, zavřete všechny instance aplikace Visual Studio.
