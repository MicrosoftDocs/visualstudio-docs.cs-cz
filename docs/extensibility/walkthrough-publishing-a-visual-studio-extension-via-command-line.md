---
title: 'Návod: Publikování rozšíření sady Visual Studio pomocí příkazového řádku | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 07/12/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d95e2fbe36a73074b97f47f6714f1fc4aa8228c
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050180"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Návod: Publikování rozšíření sady Visual Studio pomocí příkazového řádku

Tento návod ukazuje, jak publikování rozšíření sady Visual Studio na webu Visual Studio Marketplace pomocí příkazového řádku. Když přidáte rozšíření na webu Marketplace, vývojáři mohou použít [ **rozšíření a aktualizace** ](../ide/finding-and-using-visual-studio-extensions.md) dialogové okno pro procházení obsahuje nové a aktualizované rozšíření.

VsixPublisher.exe je nástroj příkazového řádku pro publikování rozšíření sady Visual Studio na webu Marketplace. Je přístupný z ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Příkazy v tomto nástroji k dispozici jsou: **publikovat**, **createPublisher**, **deletePublisher**, **deleteExtension**,  **přihlášení**, **odhlášení**.

## <a name="commands"></a>Příkazy

### <a name="publish"></a>Publikování

Publikuje rozšíření na webu Marketplace. Rozšíření může být rozšíření vsix, soubor exe nebo msi nebo odkaz. Pokud rozšíření se stejnou verzí již existuje, přepíše rozšíření. Pokud rozšíření ještě neexistuje, vytvoří nové rozšíření.

|Možnosti příkazu |Popis |
|---------|---------|
|datová část (povinné) | Buď cestu k datové části publikování nebo odkaz má použít jako "Další informace o adresu URL". |
|publishManifest (povinné) | Cesta k publikování manifestu soubor se má použít. |
|ignoreWarnings | Seznam upozornění ignorovat při publikování rozšíření. Tato upozornění se zobrazují jako zprávy příkazového řádku při publikování rozšíření. (například "VSIXValidatorWarning01, VSIXValidatorWarning02")  
|personalAccessToken | Personal Access Token PAT, který se používá k ověření vydavatele. Pokud se nezadá, je na token PAT získaných z přihlášeného uživatele. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Vytvoří vydavatele na webu Marketplace. Vydavateli protokoluje také do počítače pro budoucí akce (například odstranění a publikování rozšíření).

|Možnosti příkazu |Popis |
|---------|---------|
|displayName (povinné) | Zobrazovaný název vydavatele. |
|Název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|personalAccessToken (povinné) | Osobní přístupový Token, který se používá k ověření vydavatele. |
|shortDescription | Krátký popis vydavatele (ne soubor). |
|longDescription | Dlouhý popis vydavatele (ne soubor). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Odstraní vydavatele na webu Marketplace.

|Možnosti příkazu |Popis |
|---------|---------|
|Název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|personalAccessToken (povinné) | Osobní přístupový Token, který se používá k ověření vydavatele. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Odstraní rozšíření z webu Marketplace.

|Možnosti příkazu |Popis |
|---------|---------|
|extensionName (povinné) | Název rozšíření odstranit. |
|Název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|personalAccessToken | Osobní přístupový Token, který se používá k ověření vydavatele. Pokud se nezadá, je na token pat získaných z přihlášeného uživatele. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>přihlášení

Vydavatel přihlásí k počítači.

|Možnosti příkazu |Popis |
|---------|---------|
|personalAccessToken (povinné | Osobní přístupový Token, který se používá k ověření vydavatele. |
|Název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|Přepsat | Určuje, že se nový osobní přístupový token má se přepsat libovolného existujícího vydavatele. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>odhlášení

Protokoly vydavatele z počítače.

|Možnosti příkazu |Popis |
|---------|---------|
|Název_vydavatele (povinné) | Název vydavatele (například identifikátor). |
|ignoreMissingPublisher | Určuje, že nástroj by měl nevygeneruje chybu, pokud zadaný vydavatel není již přihlášeni. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>soubor publishManifest

PublishManifest soubor je používán **publikovat** příkazu. Představuje všechna metadata o rozšíření, která potřebuje vědět, na webu Marketplace. Pokud je rozšíření nahrává ze rozšíření VSIX, vlastnost "identity" musí mít pouze "internalName" nastavit. Je to proto, že zbývající vlastnosti "identity" se dá vygenerovat na vsixmanifest souboru. Pokud rozšíření msi a exe nebo odkaz rozšíření, uživatel musí poskytnout požadovaná pole ve vlastnosti "identity". Zbývající část manifest obsahuje informace týkající se webu Marketplace (například kategorie, zda funkce Q & A je povoleno, atd.).

Ukázkový soubor publishManifest VSIX rozšíření:

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

Soubor MSI a EXE nebo odkaz publishManifest soubor ukázka:

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

Soubory prostředků lze zadat pro vkládání věci, jako je Image v souboru readme. Například, pokud je rozšíření Markdownu dokumentu následující "Přehled":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Aby bylo možné vyřešit "images/testlogo.png" v předchozím příkladu, uživatel může poskytnout "assetFiles" v jejich publikování manifestu jako níže:

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

## <a name="publishing-walkthrough"></a>Návod pro publikování

### <a name="prerequisites"></a>Požadavky

Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Vytvoření rozšíření sady Visual Studio

V tomto případě použijeme rozšíření VSPackage výchozí, ale stejný postup platí pro každý typ rozšíření.

1. Vytvoření VSPackage v jazyce C# s názvem "TestPublish", který obsahuje příkaz nabídky. Další informace najdete v tématu [vytváření prvního rozšíření: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Balíček rozšíření

1. Rozšíření vsixmanifest aktualizujte se správnými informacemi o názvu produktu, autora a verzi.

   ![aktualizace rozšíření vsixmanifest](media/update-extension-vsixmanifest.png)

2. Vytváření rozšíření **vydání** režimu. Rozšíření teď budou zabalené jako rozšíření VSIX ve složce \bin\Release.

3. Poklepejte na položku VSIX k ověření instalace.

### <a name="test-the-extension"></a>Testování rozšíření

 Před distribucí rozšíření, sestavit a otestovat a ujistit se, že je v experimentální instanci sady Visual Studio správně nainstalované.

1. V sadě Visual Studio spusťte ladění. Chcete-li spustit experimentální instanci sady Visual Studio.

2. V experimentální instanci aplikace, přejděte **nástroje** nabídky a klikněte na tlačítko **rozšíření a aktualizace...** . Rozšíření TestPublish by se měla objevit v prostředním podokně a povolit.

3. Na **nástroje** nabídky, ujistěte se, že se zobrazí příkaz test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Publikování rozšíření na webu Marketplace pomocí příkazového řádku

1. Ujistěte se, že jste vytvořili na prodejní verzi produktu rozšíření a zda je aktuální.

2. Ujistěte se, že jste vytvořili publishmanifest.json a overview.md souborů.

3. Otevřete příkazový řádek a přejděte do adresáře \VSSDK\VisualStudioIntegration\Tools\Bin\ ${VSInstallDir}.

4. Pokud chcete vytvořit nový vydavatele, použijte následující příkaz:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Po úspěšném vytvoření vydavatele zobrazí se následující zpráva příkazového řádku:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Můžete ověřit, vytvoříte tak, že přejdete do nové vydavatele [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Chcete-li publikovat nové rozšíření, použijte následující příkaz:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Po úspěšném vytvoření vydavatele zobrazí se následující zpráva příkazového řádku:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Můžete ověřit nové rozšíření, které jste publikovali tak, že přejdete do [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Nainstalovat rozšíření z Visual Studio Marketplace

Teď, když se publikuje rozšíření, nainstalujte ho v sadě Visual Studio a ho vyzkoušeli.

1. V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace...** .

2. Klikněte na tlačítko **Online** a vyhledejte TestPublish.

3. Klikněte na tlačítko **Stáhnout**. Rozšíření se pak naplánovat pro instalaci.

4. K dokončení instalace, ukončete všechny instance sady Visual Studio.

## <a name="remove-the-extension"></a>Odebrat rozšíření

Rozšíření můžete odebrat z webu Visual Studio Marketplace a z vašeho počítače.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Odebrat rozšíření z webu Marketplace pomocí příkazového řádku

1. Pokud chcete odebrat rozšíření, použijte následující příkaz:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Úspěšné odstranění rozšíření se zobrazí následující zpráva příkazového řádku:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Odebrat rozšíření z počítače

1. V sadě Visual Studio na **nástroje** nabídky, klikněte na tlačítko **rozšíření a aktualizace...** .

2. Vyberte "MyVsixExtension" a potom klikněte na tlačítko **odinstalovat**. Rozšíření se pak být naplánovaná odinstalace.

3. K dokončení odinstalace, zavřete všechny instance sady Visual Studio.
