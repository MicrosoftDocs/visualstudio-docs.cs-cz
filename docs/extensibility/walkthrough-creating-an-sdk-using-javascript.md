---
title: 'Návod: Vytvoření sady SDK pomocí JavaScriptu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697504"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Návod: Vytvoření sady SDK pomocí JavaScriptu
Tento návod učí, jak pomocí Jazyka JavaScript vytvořit jednoduchou matematickou sadku SDK jako rozšíření sady Visual Studio (VSIX).  Návod je rozdělen do těchto částí:

- [Vytvoření projektu sady SDK rozšíření SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Vytvoření ukázkové aplikace, která používá sadu SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Pro JavaScript neexistuje žádný typ projektu knihovny tříd. V tomto návodu ukázkový *soubor aritmetic.js* je vytvořen přímo v projektu VSIX. V praxi doporučujeme nejprve sestavit a otestovat soubory JavaScriptu a CSS jako **Blank App** aplikaci pro Windows Store , než je vložíte do projektu VSIX.

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>Vytvoření projektu sady SDK rozšíření SimpleMathVSIX

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

2. V seznamu kategorií šablon vyberte v části **Visual C#** **možnost Rozšiřitelnost**a pak vyberte šablonu **projektu VSIX.**

3. V **Name** textovém poli `SimpleMathVSIX` Název zadejte a zvolte tlačítko **OK.**

4. Pokud se zobrazí **Průvodce balíčkem sady Visual Studio,** zvolte tlačítko **Další** na **úvodní** stránce a potom na stránce 1 **ze 7**zvolte tlačítko **Dokončit.**

     Přestože **se otevře Návrhář manifestu,** tento návod ponecháme jednoduchý přímo upravíme.

5. V **Průzkumníku řešení**otevřete místní nabídku souboru **source.extension.vsixmanifest** a pak zvolte **Zobrazit kód**. Tento kód slouží k nahrazení existujícího obsahu v souboru.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. V **Průzkumníku řešení**otevřete místní nabídku pro projekt **SimpleMathVSIX** a pak zvolte **Přidat** > **novou položku**.

7. V kategorii **Data** vyberte **soubor XML** `SDKManifest.xml`, pojmenujte soubor a zvolte tlačítko **Přidat.**

8. V **Průzkumníku řešení**otevřete místní nabídku pro soubor **SDKManifest.xml** a pak zvolte **Otevřít,** chcete-li soubor zobrazit v **editoru XML**.

9. Přidejte následující kód do souboru **SDKManifest.xml.**

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. V **Průzkumníku řešení**zvolte v místní nabídce souboru **SDKManifest.xml** **možnost Vlastnosti**.

11. V okně **Vlastnosti** nastavte vlastnost **Zahrnout do vSIX** na **hodnotu True**.

12. V **Průzkumníku řešení**v místní nabídce projektu **SimpleMathVSIX** zvolte **Přidat** >  `Redist`novou**složku**a pojmenujte složku .

13. Chcete-li vytvořit tuto strukturu složek, přidejte podsložky pod redist:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. V místní nabídce složky **\js\\ ** zvolte **Přidat** > **novou položku**.

15. V **části Visual C# položky**, vyberte **kategorii web** a vyberte položku **souboru JavaScript.** Pojmenujte `arithmetic.js`soubor a pak zvolte tlačítko **Přidat.**

16. Do *aritmetického*kódu vložte následující kód :

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. V **Průzkumníku řešení**v místní nabídce souboru **aritmetic.js** zvolte **Vlastnosti**. Proveďte tyto změny vlastností:

    - Nastavte **vlastnost Zahrnout do VSIX** na **hodnotu True**.

    - Nastavte vlastnost **Kopírovat do výstupního adresáře** na **Kopírovat vždy**.

18. V **Průzkumníku řešení**v místní nabídce projektu **SimpleMathVSIX** zvolte **Build**.

19. Po úspěšném dokončení sestavení zvolte v místní nabídce projektu možnost **Otevřít složku v Průzkumníkovi souborů**. Přejděte na **\bin\debug\\**a spusťte jeho `SimpleMathVSIX.vsix` instalaci.

20. Zvolte tlačítko **Instalovat** a nechte instalaci dokončit.

21. Restartujte sadu Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>Vytvoření ukázkové aplikace, která používá sadu SDK

1. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

2. V seznamu kategorií šablon vyberte v **části JavaScript** **Windows Store**a pak vyberte šablonu **Blank App** .

3. Do pole **Název** `ArithmeticUI`zadejte . Zvolte tlačítko **OK.**

4. V **Průzkumníku řešení**otevřete místní nabídku pro projekt **AritmeticUI** a pak zvolte **Přidat** > **odkaz**.

5. V **části Windows**zvolte **Rozšíření**a všimněte si, že se zobrazuje **jednoduchá matematika.**

6. Zaškrtněte políčko **Jednoduchá matematika** a pak zvolte tlačítko **OK.**

7. V **Průzkumníku řešení**si v části **Reference**všimněte, že se zobrazí odkaz **Jednoduchá matematika.** Rozbalte ji a všimněte si, že existuje složka **\js,\\ ** která obsahuje **soubor arithmetic.js**. Soubor **Arithmetic.js** můžete otevřít a ověřit, zda byl nainstalován zdrojový kód.

8. Pomocí následujícího kódu nahraďte obsah *souboru default.htm*.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. Pomocí následujícího kódu nahraďte obsah souboru *\js\default.js*.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. Nahraďte obsah souboru *\css\default.css* tímto kódem:

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. Zvolte klávesu **F5** pro sestavení a spuštění aplikace.

12. V unovém uzpo) aplikace zadejte libovolné dvě **=** čísla, vyberte operaci a pak zvolte tlačítko. Zobrazí se správný výsledek.

## <a name="see-also"></a>Viz také
- [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)
