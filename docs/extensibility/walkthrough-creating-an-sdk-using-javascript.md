---
title: 'Návod: vytvoření sady SDK pomocí JavaScriptu | Microsoft Docs'
description: Naučte se používat JavaScript k vytvoření jednoduché sady Math SDK jako rozšíření sady Visual Studio pomocí tohoto návodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b9a3d9e84731fe0c2526b69f60cdda1b1487583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080382"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Návod: vytvoření sady SDK pomocí JavaScriptu
Tento návod učí, jak pomocí JavaScriptu vytvořit jednoduchou sadu matematických SDK jako rozšíření sady Visual Studio (VSIX).  Návod je rozdělen do těchto částí:

- [Vytvoření projektu SimpleMathVSIX Extension SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Vytvoření ukázkové aplikace, která používá sadu SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  Pro JavaScript není k dispozici žádný typ projektu knihovny tříd. V tomto návodu je ukázkový soubor *arithmetic.js* vytvořen přímo v projektu VSIX. V praxi doporučujeme nejprve sestavit a otestovat soubory JavaScript a CSS jako aplikaci pro Windows Store, například pomocí šablony **prázdná aplikace** , než je vložíte do projektu VSIX.

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> Vytvoření projektu SimpleMathVSIX Extension SDK

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V seznamu kategorií šablon v části **Visual C#** vyberte **rozšiřitelnost** a potom vyberte šablonu **projektu VSIX** .

3. Do textového pole **název** zadejte `SimpleMathVSIX` a klikněte na tlačítko **OK** .

4. Pokud se zobrazí **Průvodce balíčkem sady Visual Studio** , klikněte na tlačítko **Další** na stránce **Vítejte** a pak na **stránce 1 z 7** klikněte na tlačítko **Dokončit** .

     I když se otevře **Návrhář manifestu** , Tento názorný postup je jednoduchý, protože přímo upravujeme soubor manifestu.

5. V **Průzkumník řešení** otevřete místní nabídku pro soubor **source. extension. vsixmanifest** a pak zvolte možnost **Zobrazit kód**. Pomocí tohoto kódu nahraďte existující obsah v souboru.

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

6. V **Průzkumník řešení** otevřete místní nabídku pro projekt **SimpleMathVSIX** a pak zvolte možnost **Přidat**  >  **novou položku**.

7. V kategorii **data** vyberte **soubor XML**, zadejte název souboru `SDKManifest.xml` a klikněte na tlačítko **Přidat** .

8. V **Průzkumník řešení** otevřete místní nabídku pro soubor **SDKManifest.xml** a pak zvolte možnost **otevřít** . zobrazí se soubor v **editoru XML**.

9. Do souboru **SDKManifest.xml** přidejte následující kód.

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

10. V **Průzkumník řešení** v místní nabídce souboru **SDKManifest.xml** vyberte možnost **vlastnosti**.

11. V okně **vlastnosti** nastavte vlastnost **zahrnout do VSIX** na **hodnotu true**.

12. V **Průzkumník řešení** v místní nabídce projektu **SimpleMathVSIX** zvolte možnost **Přidat**  >  **novou složku** a potom složku pojmenujte `Redist` .

13. Přidejte podsložky v rámci Redist a vytvořte tuto strukturu složek:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. V místní nabídce pro složku **\js \\** vyberte možnost **Přidat**  >  **novou položku**.

15. V části **Visual C# položky** vyberte kategorii **Web** a pak vyberte položku **soubor JavaScriptu** . Zadejte název souboru `arithmetic.js` a pak klikněte na tlačítko **Přidat** .

16. Do *arithmetic.js* vložte následující kód:

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

17. V **Průzkumník řešení** v místní nabídce souboru **arithmetic.js** vyberte možnost **vlastnosti**. Nastavit tyto změny vlastností:

    - Nastavte vlastnost **Zahrnout v VSIX** na **hodnotu true**.

    - Vlastnost **Kopírovat do výstupního adresáře** nastavte na hodnotu **vždy kopírovat**.

18. V **Průzkumník řešení** v místní nabídce projektu **SimpleMathVSIX** vyberte možnost **sestavit**.

19. Po úspěšném dokončení sestavení v místní nabídce projektu vyberte možnost **Otevřít složku v Průzkumníku souborů**. Přejděte na **\bin\debug \\** a spusťte `SimpleMathVSIX.vsix` instalaci.

20. Klikněte na tlačítko **nainstalovat** a nechte instalaci dokončeno.

21. Restartujte Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> Vytvoření ukázkové aplikace, která používá sadu SDK

1. Na panelu nabídek vyberte **soubor**  >  **Nový**  >  **projekt**.

2. V seznamu kategorií šablon v části **JavaScript** vyberte **Windows Store** a pak vyberte šablonu **prázdná aplikace** .

3. Do pole **název** zadejte `ArithmeticUI` . Klikněte na tlačítko **OK** .

4. V **Průzkumník řešení** otevřete místní nabídku pro projekt **ArithmeticUI** a pak zvolte možnost **Přidat**  >  **odkaz**.

5. V části **Windows** vyberte **rozšíření** a Všimněte si, že se zobrazí **jednoduché matematické** .

6. Zaškrtněte políčko **jednoduché matematické** políčko a pak klikněte na tlačítko **OK** .

7. V **Průzkumník řešení** v části **References** si všimněte, že se zobrazí **jednoduchý matematický** odkaz. Rozbalte ho a Všimněte si, že existuje **Složka \\ \js** , která zahrnuje **arithmetic.js**. Můžete otevřít **arithmetic.js** a potvrdit, že byl váš zdrojový kód nainstalován.

8. K nahrazení obsahu *default.htm* použijte následující kód.

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

9. K nahrazení obsahu *\js\default.js* použijte následující kód.

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

10. Nahraďte obsah *\css\default.CSS* tímto kódem:

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

11. Kliknutím na klávesu **F5** sestavíte a spustíte aplikaci.

12. V uživatelském rozhraní aplikace zadejte dvě čísla, vyberte operaci a pak klikněte na **=** tlačítko. Zobrazí se správný výsledek.

## <a name="see-also"></a>Viz také
- [Vytvoření sady SDK (Software Development Kit)](../extensibility/creating-a-software-development-kit.md)
