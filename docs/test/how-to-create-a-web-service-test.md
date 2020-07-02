---
title: Vytvoření testu webové služby
ms.date: 06/30/2020
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, creating Web service tests
- Web services [Visual Studio ALM], creating
- service tests, Web
ms.assetid: fbcd57ee-06ad-4260-8694-09f8e0f93e39
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9934f48e6d5900a418995eb96d357b4ea1ea532f
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814756"
---
# <a name="how-to-create-a-web-service-test"></a>Postupy: Vytvoření testu webové služby

K testování webových služeb můžete použít test výkonnosti webu. Pomocí možností **Vložení požadavku** a **vložení žádosti o webovou službu** můžete přizpůsobit jednotlivé požadavky v **Editor testu výkonnosti webu** k vyhledání stránek webové služby. Obvykle tyto stránky ve webové aplikaci nezobrazujete. Pro přístup k těmto stránkám je tedy nutné přizpůsobit požadavek.

>[!NOTE]
> Funkce webového výkonu a zátěžového testu je ve Visual Studiu 2019 zastaralá. Pro Application Insights jsou webové testy s více kroky závislé na souborech WebTest sady Visual Studio. Bylo [oznámeno](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/) , že Visual Studio 2019 bude poslední verzí s funkcí webového testu. Je důležité si uvědomit, že i když nebudou přidány žádné nové funkce, funkce webového testu v aplikaci Visual Studio 2019 je stále nadále podporována a bude nadále podporována během životního cyklu podpory produktu. Tento Azure Monitor produktový tým se zabývá otázkami ohledně [budoucích testů dostupnosti](https://github.com/MicrosoftDocs/azure-docs/issues/26050#issuecomment-468814101)s více kroky.

**Požadavky**

Visual Studio Enterprise

## <a name="to-create-a-simple-web-service"></a>Vytvoření jednoduché webové služby

Chcete-li otestovat, můžete použít vlastní webovou službu nebo použít šablonu základní webové služby (ASMX), která je součástí sady Visual Studio. Vytvoření jednoduché webové služby pomocí této šablony:

1. V aplikaci Visual Studio vytvořte nový projekt pomocí šablony ASP.NET Web Application (.NET Framework) a po zobrazení výzvy vyberte **prázdnou** šablonu. Zadejte název a vytvořte projekt.

1. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu, zvolte možnost **Přidat**  >  **novou položku**a pak zvolte možnost **Webová služba (asmx)**. Přidejte webovou službu.

1. Otevřete *WebService1. asmx* a nahraďte výchozí `HelloWorld` webovou metodu následujícím kódem.

   ```csharp
   public string HelloWorld(string str)
   {
      return "Hello, " + str;
   }
   ```

## <a name="install-the-load-testing-component"></a>Instalace komponenty zátěžového testování

Pokud ještě nemáte nainstalovanou součást Performance Test Tools a nástroj pro testování zatížení, budete ji muset nainstalovat pomocí Instalační program pro Visual Studio.

1. V nabídce **Start** systému Windows otevřete **instalační program pro Visual Studio** . Můžete k němu také přistupovat v aplikaci Visual Studio z dialogového okna Nový projekt nebo výběrem **Možnosti**  >  **získat nástroje a funkce** z panelu nabídek.

1. V **instalační program pro Visual Studio**klikněte na kartu **jednotlivé součásti** a přejděte dolů k části **ladění a testování** . Vyberte **Nástroje pro testování výkonu a zatížení webu**.

   ![Komponenta Performance and Load Test Tools](media/web-perf-load-testing-tools-component.png)

1. Klikněte na tlačítko **Upravit** .

   Komponenta Performance and Load Test Tools je nainstalována.

## <a name="create-a-web-test-project"></a>Vytvoření projektu webového testu

Webový test vyžaduje šablonu projektu webového výkonu a zátěžového testu. V této části vytvoříme projekt zátěžového testu C#. V případě potřeby můžete také vytvořit projekt Visual Basic zátěžového testu.

::: moniker range="vs-2017"

1. Otevřete sadu Visual Studio.

   Pokud používáte šablonu ukázkové webové služby (ASMX), můžete přidat projekt webového testu do stejného řešení.

2. Z řádku nabídek vyberte **soubor** > **Nový** > **projekt** .

   Otevře se dialogové okno **Nový projekt** .

3. V dialogovém okně **Nový projekt** rozbalte položku **nainstalované** a **Visual C#** a poté vyberte kategorii **test** . Vyberte šablonu **projekt webového výkonu a zátěžového testu** .

   ![Šablona projektu testování výkonu webu a zátěžového testu](media/web-perf-load-test-project-template.png)

4. Zadejte název projektu, pokud nechcete použít výchozí název, a pak zvolte **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otevřete sadu Visual Studio.

   Pokud používáte šablonu ukázkové webové služby (ASMX), můžete přidat projekt webového testu do stejného řešení.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **webový test** a potom vyberte šablonu **Performance test a zátěžový test projektu \[ nepoužívané]** pro C#. Zvolte **Další**.

4. Zadejte název projektu, pokud nechcete použít výchozí název, a pak zvolte **vytvořit**.

::: moniker-end

   Visual Studio vytvoří projekt a zobrazí soubory v **Průzkumník řešení**. Projekt zpočátku obsahuje jeden soubor webového testu s názvem *WebTest1. webtest*.

## <a name="to-test-a-web-service"></a>Testování webové služby

1. Spusťte webovou službu a v případě potřeby vyberte možnost **zastavit** pro pozastavení služby.

1. V projektu webového testu otevřete *WebTest1. webtest*, který otevře Editor testu výkonnosti webu. V editoru testů klikněte pravým tlačítkem na test výkonnosti webu a vyberte možnost **Přidat požadavek webové služby**.

1. Do vlastnosti **Adresa URL** nového požadavku zadejte název webové služby, například **https://localhost:44318/WebService1.asmx** .

1. Pro webovou službu otevřete samostatnou relaci prohlížeče a na panelu nástrojů **adresa** zadejte adresu URL stránky *. asmx* . V horní části webové stránky vyberte metodu, kterou chcete testovat, a zkontrolujte zprávu protokolu SOAP. (V ukázkové webové službě je metoda HelloWorld.) Po otevření metody vidíte, že obsahuje `SOAPAction` .

1. V **Editor testu výkonnosti webu**klikněte pravým tlačítkem myši na požadavek a výběrem **Přidat hlavičku** přidejte novou hlavičku. Do vlastnosti **název** zadejte `SOAPAction` . Do vlastnosti **hodnota** zadejte hodnotu, která se zobrazí v `SOAPAction` , například *http://tempuri.org/HelloWorld* .

1. Rozbalte uzel adresa URL v editoru testů, vyberte uzel **tělo řetězce** a v vlastnosti **typ obsahu** zadejte hodnotu `text/xml` .

1. V kroku 4 se vraťte do prohlížeče, vyberte část XML požadavku SOAP ze stránky popis webové služby a zkopírujte ji do schránky.

   Obsah kódu XML je podobný následujícímu příkladu:

     ```xml
     <?xml version="1.0" encoding="utf-8"?>
     <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
       <soap:Body>
         <HelloWorld xmlns="http://tempuri.org/">
           <str>string</str>
         </HelloWorld>
       </soap:Body>
     </soap:Envelope>
     ```

1. Vraťte se do Editor testu výkonnosti webu a potom zvolte tři tečky **(...)** ve vlastnosti **tělo řetězce** . Vložte obsah schránky do vlastnosti.

1. Nahraďte všechny zástupné hodnoty v XML platnými hodnotami tak, aby test mohl projít. V předchozím příkladu byste nahradili instanci `string` s názvem.

1. Klikněte pravým tlačítkem na požadavek webové služby a vyberte **Přidat parametr QueryString adresy URL**.

1. Parametru řetězce dotazu přiřaďte název a hodnotu. V předchozím příkladu je název `op` a hodnota je `HelloWorld` . Tím se identifikuje operace webové služby, která se má provést.

    > [!NOTE]
    > Datovou vazbu v těle protokolu SOAP můžete použít k nahrazení libovolné zástupné hodnoty hodnotami vázanými daty pomocí `{{DataSourceName.TableName.ColumnName}}` syntaxe.

1. Spusťte test. V horním podokně **prohlížeče webového výkonu výsledky testů**vyberte požadavek webové služby. V dolním podokně vyberte kartu **webový prohlížeč** . Zobrazí se kód XML vrácený webovou službou a výsledky jakékoli operace.

   Vyhledejte výsledky pro požadavek webové služby.

## <a name="see-also"></a>Viz také:

- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
