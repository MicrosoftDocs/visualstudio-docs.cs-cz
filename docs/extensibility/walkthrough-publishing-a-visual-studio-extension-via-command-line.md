---
title: Publikovat rozšíření pomocí příkazového řádku
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697129"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Návod: Publikování rozšíření sady Visual Studio pomocí příkazového řádku

Tento návod ukazuje, jak publikovat rozšíření Sady Visual Studio na webu Visual Studio Marketplace pomocí příkazového řádku. Když přidáte rozšíření na Marketplace, vývojáři mohou použít rozšíření [**a aktualizace**](../ide/finding-and-using-visual-studio-extensions.md) dialogové okno procházet tam pro nové a aktualizované rozšíření.

VsixPublisher.exe je nástroj příkazového řádku pro publikování rozšíření sady Visual Studio na marketplace. Lze k němu získat přístup z programu ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Příkazy jsou k dispozici na tomto nástroji jsou: **publikovat**, **createPublisher**, **deletePublisher**, **deleteExtension**, **přihlášení**, **odhlášení**.

## <a name="commands"></a>Příkazy

### <a name="publish"></a>publish

Publikuje rozšíření marketplace. Rozšíření může být vsix, exe/msi soubor nebo odkaz. Pokud rozšíření již existuje se stejnou verzí, přepíše rozšíření. Pokud rozšíření ještě neexistuje, vytvoří nové rozšíření.

|Možnosti příkazu |Popis |
|---------|---------|
|užitečné zatížení (povinné) | Buď cesta k datové části publikovat nebo odkaz použít jako "více informací URL". |
|publishManifest (povinné) | Cesta k souboru manifestu publikování, který chcete použít. |
|ignoreWarnings | Seznam upozornění ignorovat při publikování rozšíření. Tato upozornění jsou při publikování rozšíření zobrazena jako zprávy příkazového řádku. (například "VSIXValidatorWarning01, VSIXValidatorWarning02")
|aplikace personalAccessToken | Osobní přístupový token (PAT), který se používá k ověření vydavatele. Pokud není poskytnuta, PAT je získán od přihlášených uživatelů. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Vytvoří vydavatele na webu Marketplace. Také přihlásí vydavatele do počítače pro budoucí akce (například odstranění nebo publikování rozšíření).

|Možnosti příkazu |Popis |
|---------|---------|
|displayName (povinné) | Zobrazovaný název vydavatele. |
|název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|personalAccessToken (povinné) | Osobní přístupový token, který se používá k ověření vydavatele. |
|shortDescription | Krátký popis vydavatele (nikoli souboru). |
|longDescription | Dlouhý popis vydavatele (nikoli souboru). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>odstranitvydavatel

Odstraní vydavatele na webu Marketplace.

|Možnosti příkazu |Popis |
|---------|---------|
|název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|personalAccessToken (povinné) | Osobní přístupový token, který se používá k ověření vydavatele. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Odstraní rozšíření z webu Marketplace.

|Možnosti příkazu |Popis |
|---------|---------|
|extensionName (povinné) | Název rozšíření odstranit. |
|název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|aplikace personalAccessToken | Osobní přístupový token, který se používá k ověření vydavatele. Pokud není k dispozici, pat je získán od přihlášených uživatelů. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>přihlášení

Přihlásí vydavatele do počítače.

|Možnosti příkazu |Popis |
|---------|---------|
|personalAccessToken (povinné | Osobní přístupový token, který se používá k ověření vydavatele. |
|název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|Přepsat | Určuje, že všechny existující vydavatele by měly být přepsány pomocí nového osobního přístupového tokenu. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Zaznamená vydavatele ze zařízení.

|Možnosti příkazu |Popis |
|---------|---------|
|název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|ignoreMissingPublisher | Určuje, že nástroj by se neměl chybově, pokud zadaný vydavatel ještě není přihlášen. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest soubor

Příkaz publishManifest používá soubor **publish.** Představuje všechna metadata o rozšíření, které marketplace potřebuje znát. Pokud rozšíření, které se nahrává, pochází z rozšíření VSIX, vlastnost "identity" musí mít pouze nastavenou "internalName". Důvodem je, že zbytek "identity" vlastnosti mohou být generovány ze souboru vsixmanifest. Pokud rozšíření je msi/exe nebo rozšíření propojení, uživatel musí poskytnout požadovaná pole ve vlastnosti "identity". Zbytek manifestu obsahuje informace specifické pro Marketplace (například kategorie, zda je povolena Q&A atd.).

Přípona VSIX publishManifest ukázka souboru:

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

Ukázka souboru manifestu msi/exe nebo link:

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

## <a name="asset-files"></a>Soubory datových zdrojů

Soubory datových zdrojů mohou být poskytnuty pro vkládání věcí, jako jsou obrázky do souboru readme. Například pokud rozšíření má následující "přehled" Markdown dokument:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Chcete-li vyřešit "images/testlogo.png" v předchozím příkladu, uživatel může poskytnout "assetFiles" v jejich manifestu publikování, jako je níže:

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

Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Vytvoření rozšíření sady Visual Studio

V takovém případě použijeme výchozí rozšíření VSPackage, ale stejné kroky platí pro všechny druhy rozšíření.

1. Vytvořte VSPackage v C# s názvem "TestPublish", který má příkaz nabídky. Další informace naleznete [v tématu Vytvoření prvního rozšíření: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Zabalte rozšíření

1. Aktualizujte rozšíření vsixmanifest se správnými informacemi o názvu produktu, autorovi a verzi.

   ![aktualizovat rozšíření vsixmanifest](media/update-extension-vsixmanifest.png)

2. Vytvořte rozšíření v režimu **vydání.** Nyní bude vaše rozšíření zabaleno jako VSIX ve složce \bin\Release.

3. Instalaci můžete ověřit poklepáním na vsix.

### <a name="test-the-extension"></a>Otestujte rozšíření

 Před distribucí rozšíření, sestavení a testování, ujistěte se, že je správně nainstalován v experimentální instanci sady Visual Studio.

1. V sadě Visual Studio spusťte ladění. otevřete experimentální instanci sady Visual Studio.

2. V experimentální instanci přejděte do nabídky **Nástroje** a klikněte na **Rozšíření a aktualizace...**. Rozšíření TestPublish by se mělo zobrazit v prostředním podokně a být povoleno.

3. V nabídce **Nástroje** zkontrolujte, zda se zobrazí příkaz test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publikování rozšíření na Marketplace pomocí příkazového řádku

1. Ujistěte se, že jste vytvořili verzi rozšíření a že je aktuální.

2. Ujistěte se, že jste vytvořili souborpublishmanifest.json a overview.md.

3. Otevřete příkazový řádek a přejděte do adresáře ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Chcete-li vytvořit nového vydavatele, použijte následující příkaz:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Při úspěšném vytvoření vydavatele se zobrazí následující zpráva příkazového řádku:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Nového vydavatele, kterého jste vytvořili, můžete ověřit přechodem na [tržiště Sady Visual Studio.](https://marketplace.visualstudio.com/manage/publishers)

7. Chcete-li publikovat nové rozšíření, použijte následující příkaz:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Při úspěšném vytvoření vydavatele se zobrazí následující zpráva příkazového řádku:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Nové rozšíření, které jste publikovali, můžete ověřit přechodem na [tržiště sady Visual Studio.](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Instalace rozšíření z webu Visual Studio Marketplace

Teď, když je rozšíření publikováno, nainstalujte ho do sady Visual Studio a otestujte jej tam.

1. V sadě Visual Studio klikněte v nabídce **Nástroje** na **položku Rozšíření a aktualizace...**.

2. Klikněte na **Online** a vyhledejte TestPublish.

3. Klepněte na tlačítko **Stáhnout**. Rozšíření pak bude naplánováno pro instalaci.

4. Chcete-li dokončit instalaci, zavřete všechny instance sady Visual Studio.

## <a name="remove-the-extension"></a>Odebrání rozšíření

Rozšíření můžete odebrat z webu Visual Studio Marketplace a z počítače.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Odebrání rozšíření z webu Marketplace pomocí příkazového řádku

1. Chcete-li rozšíření odebrat, použijte následující příkaz:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Při úspěšném odstranění rozšíření se zobrazí následující zpráva příkazového řádku:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Odebrání rozšíření z počítače

1. V sadě Visual Studio klikněte v nabídce **Nástroje** na **položku Rozšíření a aktualizace**.

2. Vyberte možnost MyVsixExtension a klepněte na tlačítko **Odinstalovat**. Rozšíření pak bude naplánováno na odinstalaci.

3. Chcete-li provést odinstalaci, zavřete všechny instance sady Visual Studio.
