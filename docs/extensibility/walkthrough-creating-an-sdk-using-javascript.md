---
title: 'Návod: Vytvoření sady SDK pomocí jazyka JavaScript | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1be1cf15e1f43af5999d4d65a5342d9c7b46da25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884066"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Návod: Vytvoření sady SDK pomocí jazyka JavaScript
Tento návod se naučíte vytvořit jednoduché matematické sadu SDK jako Visual Studio Extension (VSIX) pomocí jazyka JavaScript.  Návod je rozdělen na tyto části:  
  
- [Chcete-li vytvořit projekt SimpleMathVSIX rozšíření sady SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
- [Vytvořte ukázkovou aplikaci, která používá sadu SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
  Pro jazyk JavaScript neexistuje žádný typ projektu knihovny tříd. V tomto podrobném návodu, ukázka *arithmetic.js* soubor je vytvořen přímo v projektu VSIX. V praxi, doporučujeme vám nejdřív sestavení a testování souborů JavaScript a CSS jako aplikace Windows Store – například s použitím **prázdnou aplikaci** šablony – předtím, než začleníte v projektu VSIX.  
  
## <a name="prerequisites"></a>Požadavky  
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="createSimpleMathVSIX"></a> Chcete-li vytvořit projekt SimpleMathVSIX rozšíření sady SDK  
  
1.  V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
2.  V seznamu kategorií šablon pod **Visual C#** vyberte **rozšiřitelnost**a pak vyberte **projekt VSIX** šablony.  
  
3.  V **název** text zadejte `SimpleMathVSIX` a zvolte **OK** tlačítko.  
  
4.  Pokud **Průvodce nastavením programu Visual Studio balíček** se zobrazí, zvolte **Další** tlačítko **úvodní** stránky a pak na **stránka 1 z 7**, zvolte **Dokončit** tlačítko.  
  
     I když **Manifest Designer** se otevře, budeme Tento názorný postup jednoduché tak, že upravíte soubor manifestu přímo.  
  
5.  V **Průzkumníka řešení**, otevřete místní nabídku **source.extension.vsixmanifest** souboru a klikněte na tlačítko **zobrazit kód**. Pomocí tohoto kódu můžete nahradit existující obsah v souboru.  
  
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
  
6.  V **Průzkumníka řešení**, otevřete místní nabídku **SimpleMathVSIX** projektu a klikněte na tlačítko **přidat** > **nová položka**.  
  
7.  V **Data** vyberte **soubor XML**, pojmenujte soubor `SDKManifest.xml`a zvolte **přidat** tlačítko.  
  
8.  V **Průzkumníku řešení**, otevřete místní nabídku **SDKManifest.xml** souboru a klikněte na tlačítko **otevřete** k zobrazení souboru v **editoru XML**.  
  
9. Přidejte následující kód, který **SDKManifest.xml** souboru.  
  
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
  
10. V **Průzkumníka řešení**, v místní nabídce pro **SDKManifest.xml** souboru, zvolte **vlastnosti**.  
  
11. V **vlastnosti** okno, nastaveno **zahrnout do VSIX** vlastnost **True**.  
  
12. V **Průzkumníka řešení**, v místní nabídce pro **SimpleMathVSIX** projektu, zvolte **přidat** > **novou složku**, a potom zadejte název složky `Redist`.  
  
13. Přidáte podsložky Redist vytvořit tuto strukturu složek:  
  
     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*  
  
14. V místní nabídce pro **\js\\**  složky, zvolte **přidat** > **nová položka**.  
  
15. V části **položky Visual C#**, vyberte **webové** kategorie a pak vyberte **soubor JavaScript** položky. Název souboru `arithmetic.js`a klikněte na tlačítko **přidat** tlačítko.  
  
16. Vložte následující kód do *arithmetic.js*:  
  
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
  
17. V **Průzkumníka řešení**, v místní nabídce pro **arithmetic.js** souboru, zvolte **vlastnosti**. Tyto změny vlastností:  
  
    -   Nastavte **zahrnout do VSIX** vlastnost **True**.  
  
    -   Nastavte **kopírovat do výstupního adresáře** vlastnost **vždy Kopírovat**.  
  
18. V **Průzkumníka řešení**, v místní nabídce pro **SimpleMathVSIX** projektu, zvolte **sestavení**.  
  
19. Po dokončení sestavení úspěšně, v místní nabídce projektu zvolte **otevřít složku v Průzkumníku souborů**. Přejděte do **\bin\debug\\**a spusťte `SimpleMathVSIX.vsix` k její instalaci.  
  
20. Zvolte **nainstalovat** tlačítko a umožňují instalace dokončena.  
  
21. Restartujte sadu Visual Studio.  
  
##  <a name="createSampleApp"></a> Vytvořte ukázkovou aplikaci, která používá sadu SDK  
  
1. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.  
  
2. V seznamu kategorií šablon pod **JavaScript**vyberte **Windows Store**a pak vyberte **prázdnou aplikaci** šablony.  
  
3. V **název** zadejte `ArithmeticUI`. Zvolte **OK** tlačítko.  
  
4. V **Průzkumníka řešení**, otevřete místní nabídku **ArithmeticUI** projektu a klikněte na tlačítko **přidat** > **odkaz**.  
  
5. V části **Windows**, zvolte **rozšíření**a Všimněte si, že **jednoduchých matematických** se zobrazí.  
  
6. Vyberte **jednoduchých matematických** zaškrtněte políčko a klikněte na tlačítko **OK** tlačítko.  
  
7. V **Průzkumníka řešení**v části **odkazy**, Všimněte si, že **jednoduchých matematických** odkazu se zobrazí. Rozbalte ho a Všimněte si, že je **\js\\**  složky, která obsahuje **arithmetic.js**. Můžete otevřít **arithmetic.js** potvrďte, že váš zdrojový kód byl nainstalován.  
  
8. Pomocí následujícího kódu nahraďte obsah *default.htm*.  
  
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
  
9. Pomocí následujícího kódu nahraďte obsah *\js\default.js*.  
  
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
  
10. Nahraďte obsah *\css\default.css* s tímto kódem:  
  
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
  
11. Zvolte **F5** klíče pro sestavení a spuštění aplikace.  
  
12. V Uživatelském rozhraní aplikace, zadejte jakékoli dvě čísla, vyberte operaci a klikněte na tlačítko **=** tlačítko. Správný výsledek se zobrazí.  
  
## <a name="see-also"></a>Viz také:  
 [Vytvořit Software Development Kit](../extensibility/creating-a-software-development-kit.md)
