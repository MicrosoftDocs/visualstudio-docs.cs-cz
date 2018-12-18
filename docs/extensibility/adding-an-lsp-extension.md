---
title: Přidání rozšíření protokol jazyka serveru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/14/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f2710693c7dae7c4238f9f31fbe8065d6864a19
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672961"
---
# <a name="add-a-language-server-protocol-extension"></a>Přidat příponu protokol jazyka serveru

Protokol jazyka serveru (LSP) je společný protokol ve formátu JSON RPC v2.0, používají k zajištění funkce služby pro různé editory kódu jazyka. Pomocí protokolu, vývojáři psát jeden jazyk serveru zadejte jazykové funkce služby, jako je IntelliSense, Diagnostika chyb, najít všechny odkazy, atd. a různé editory kódu, které podporují LSP. Tradičně jazykových služeb v sadě Visual Studio můžete přidat buď pomocí souborů gramatiky TextMate poskytnout základní funkce, jako je například zvýraznění syntaxe nebo zápisem vlastního jazykových služeb pomocí úplné sady rozhraní API pro rozšíření sady Visual Studio k poskytují podrobnější údaje. Nyní podpora LSP nabízí třetí možnost.

![Služba Protokol jazyka serveru v sadě Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protokol jazyka serveru

![implementaci protokol jazyka serveru](media/lsp-implementation.png)

Tento článek popisuje, jak vytvořit rozšíření sady Visual Studio, který využívá jazyk na základě LSP server. Předpokládá, že jste již vytvořili serveru jazyk na základě LSP a chcete jenom ji integrovat do sady Visual Studio.

Pro podporu Visual Studia jazyk servery můžou klienti komunikovat klienta (Visual Studio) prostřednictvím každý použitý mechanizmus přenosu na základě datového proudu, například:

* Standardní vstupní/výstupní datové proudy
* Pojmenované kanály
* Sokety (pouze TCP)

Záměrem LSP a podporu v sadě Visual Studio je připojení jazykovými službami, které nejsou součástí produktu Visual Studio. Není určena k rozšíření existující jazykových služeb (jako je C#) v sadě Visual Studio. Rozšířit existující jazyky, najdete v tématu Průvodce rozšíření služeb jazyka (například [platformě .NET Compiler Platform "Roslyn"](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

Další informace o samotný protokol, naleznete v dokumentaci [tady](https://github.com/Microsoft/language-server-protocol).

Další informace o tom, jak vytvořit ukázkový server jazyka nebo jak integrovat existující server jazyk do Visual Studio Code, naleznete v dokumentaci [tady](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-features-supported"></a>Protokol serveru funkcí jazyka podporovaná

Následující funkce LSP jsou podporovány v sadě Visual Studio, pokud:

Zpráva | Má podporu v sadě Visual Studio
--- | ---
Inicializace | Ano
inicializován | Ano
vypnutí | Ano
ukončení | Ano
$/ cancelRequest | Ano
okno/Zobrazitzpravu | Ano
okno/showMessageRequest | Ano
okno/logMessage | Ano
telemetrie a událostí |
Klient/registerCapability |
Klient/unregisterCapability |
pracovní prostor/didChangeConfiguration | Ano
pracovní prostor/didChangeWatchedFiles | Ano
pracovní prostor/symbol | Ano
pracovní prostor/executeCommand | Ano
pracovní prostor/applyEdit | Ano
textDocument/publishDiagnostics | Ano
textDocument/didOpen | Ano
textDocument/didChange | Ano
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | Ano
textDocument/didClose | Ano
textDocument/dokončení | Ano
dokončení nebo řešení | Ano
textDocument/při najetí myší | Ano
textDocument/signatureHelp | Ano
textDocument/odkazy | Ano
textDocument/documentHighlight | Ano
textDocument/documentSymbol | Ano
textDocument/formátování | Ano
textDocument/rangeFormatting | Ano
textDocument/onTypeFormatting |
textDocument/definici | Ano
textDocument/codeAction | Ano
textDocument/codeLens |
codeLens nebo řešení |
textDocument/documentLink |
documentLink nebo řešení |
textDocument/přejmenování | Ano

## <a name="getting-started"></a>Začínáme

> [!NOTE]
> Od verze Visual Studio 15.8 ve verzi Preview 3 podpora pro běžné protokol jazyka serveru je integrovaná do sady Visual Studio.  Pokud jste vytvořili LSP rozšíření pomocí našich ve verzi preview [jazyk serveru klienta VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) verze, přestanou fungovat až do jste upgradovali na 15,8 ve verzi Preview 3 nebo vyšší.  Budete muset následujícím postupem získejte rozšíření LSP znovu pracovat:
>
> 1. Odinstalujte Microsoft Visual Studio jazyk serveru protokolu Preview VSIX.  Počínaje 15,8 ve verzi Preview 4, pokaždé, když provedete upgrade v sadě Visual Studio jsme bude automaticky rozpoznávat a odebrat náhled VSIX pro vás během procesu upgradu.
>
> 2. Aktualizujte referenci Nuget na nejnovější verzi – ve verzi preview pro [LSP balíčky](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Odeberte závislost na Microsoft Visual Studio jazyka serveru protokolu ve verzi Preview VSIX v manifestu VSIX.
>
> 4. Ujistěte se, že VSIX určí jako dolní mez pro cíl instalace Visual Studio 15.8 ve verzi Preview 3.
>
> 5. Znovu sestavte a znovu nasadit.

### <a name="create-a-vsix-project"></a>Vytvořte projekt VSIX

Chcete-li vytvořit rozšíření služeb jazyka pomocí serveru jazyk na základě LSP, nejprve ujistěte se, že máte **vývoj rozšíření sady Visual Studio** nainstalovaná pro vaši instanci VS úloha.

Další tak, že přejdete na vytvoření nové prázdné VSIXProject **souboru** > **nový projekt** > **Visual C#**  >   **Rozšiřitelnost** > **projekt VSIX**:

![Vytvoření projektu vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Instalace jazyků serveru a modulu runtime

Ve výchozím nastavení rozšíření vytvořili za účelem podpory jazyka založeného na LSP servery v sadě Visual Studio nebude obsahovat samotné servery jazyka nebo modulů runtime potřebné ke spuštění je. Vývojáři rozšíření jsou odpovídá za distribuci servery jazyka a moduly runtime potřeba. Chcete-li to provést několika způsoby:

* Jazyk serverů může být vložen do VSIX jako soubory obsahu.
* Vytvořit soubor MSI instalace serveru pro jazyk a/nebo potřeby moduly runtime.
* Pokyny na webu Marketplace informující uživatele získání servery moduly runtime a jazyk.

### <a name="textmate-grammar-files"></a>Soubory gramatiky TextMate

LSP neobsahuje specifikaci o tom, jak poskytnout zabarvení textu pro jazyky. Pokud chcete zadat vlastní barevné zvýraznění pro jazyky v sadě Visual Studio, vývojáři rozšíření můžete použít soubor gramatiky TextMate. Chcete-li přidat vlastní soubory TextMate gramatiky nebo motivu, postupujte takto:

1. Vytvořte složku s názvem "Gramatiky" v rozšíření (nebo může být jakýkoli název, který zvolíte).

2. Uvnitř *gramatiky* složky, zahrnutí všech  *\*.tmlanguage*,  *\*.plist*,  *\*.tmtheme*, nebo  *\*.json* souborů byste chtěli, které poskytuje vlastní zabarvení.

3. Klikněte pravým tlačítkem na požadované soubory, vyberte **vlastnosti**. Změnit **sestavení** akce **obsahu** a **zahrnout do VSIX** vlastnost na hodnotu true.

4. Vytvoření *.pkgdef* soubor a přidá řádek podobný tomuto:

   ```xml
   [$RootKey$\TextMate\Repositories]
   "MyLang"="$PackageFolder$\Grammars"
   ```

5. Klikněte pravým tlačítkem na požadované soubory, vyberte **vlastnosti**. Změnit **sestavení** akce **obsahu** a **zahrnout do VSIX** vlastnost na hodnotu true.

Po dokončení předchozích kroků *gramatiky* přidat složku k instalaci balíčku adresář jako zdrojové úložiště s názvem 'MyLang' ("MyLang" je pouze název pro odstraňování mnohoznačnosti a může obsahovat libovolný jedinečný řetězec). Všechny gramatiku (*.tmlanguage* soubory) a soubory motivů (*.tmtheme* souborů) v tomto adresáři, vyberou se jako možnosti a mají přednost před integrované gramatik TextMate součástí. Pokud soubor gramatiky deklarované rozšíření odpovídají příponám souborů otevírané, TextMate přesune se krokování.

## <a name="create-a-simple-language-client"></a>Vytvořte Jednoduchý jazyk klienta

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Hlavní rozhraní - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Po vytvoření projektu VSIX, přidejte následující balíčky NuGet do projektu:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Když zavést závislost na balíčku NuGet. Po dokončení předchozích kroků, Newtonsoft.Json a StreamJsonRpc balíčky přidají do svého projektu také. **Pokud si nejste jisti, že tyto nové verze se nainstaluje na verzi sady Visual Studio neaktualizují tyto balíčky, které vaše rozšíření cílí**. Sestavení nebudou zahrnuty do VSIX – místo toho se vybere si z adresáře instalace sady Visual Studio. Pokud odkazujete na novější verzi sestavení, než jaká je nainstalována v počítači uživatele, rozšíření *nebude fungovat*.

Potom můžete vytvořit novou třídu, která implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) rozhraní, hlavní rozhraní, které jsou potřebné pro připojení k serveru jazyk na základě LSP klienty jazyka.

Tady je ukázka:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Hlavní metody, které je třeba k implementaci jsou [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) a [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) se volá při načtení rozšíření sady Visual Studio a jazyka serveru je připraven ke spuštění. V této metodě, můžete vyvolat [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) okamžitě na signál, že jazyk serveru měly být spuštěny, nebo můžete provést další logiku a vyvolání delegáta [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) později. **K aktivaci serveru jazyk, je nutné volat StartAsync v určitém okamžiku.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) je metoda nakonec vyvolána voláním [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegovat; obsahuje logiku pro spuštění jazyk serveru a připojení k němu. Objekt připojení, který obsahuje datové proudy pro zápis do serveru a čtení ze serveru musí být vrácena. Jakýchkoli výjimek jsou zachyceny a zobrazí uživateli zprávou informační panel v sadě Visual Studio.

### <a name="activation"></a>Aktivace

Jakmile je třída jazyka klienta, budete muset definovat dva atributy, aby se definovat, jak ho načíst do sady Visual Studio, který se aktivuje:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio používá [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) ke správě svých bodů rozšiřitelnosti. [Exportovat](/dotnet/api/system.componentmodel.composition.exportattribute) atribut označuje do sady Visual Studio, že tato třída nenačítají jako rozšiřovacím bodem a načíst v příslušnou dobu.

Použití rozhraní MEF, musíte také definovat MEF jako prostředek v manifestu VSIX.

Otevřete návrháře manifestu VSIX a přejděte **prostředky** kartu:

![Přidat prostředek MEF](media/lsp-add-asset.png)

Klikněte na nový a vytvoření nového prostředku:

![definování MEF asset](media/lsp-define-asset.png)

* **Typ**: Microsoft.VisualStudio.MefComponent
* **Zdroj**: projekt v aktuálním řešení
* **Projekt**: [projekt]

### <a name="content-type-definition"></a>Definice typu obsahu

Aktuálně je jediný způsob, jak načíst vaše rozšíření jazyka založeného na LSP serveru podle typu obsahu souboru. To znamená při definování třída klienta jazyk (která implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), budete muset určit typy souborů, které, je-li otevřít, způsobí, že rozšíření pro načtení. Pokud jsou otevřené žádné soubory, které odpovídají definované typ obsahu, pak vaše rozšíření se nenačte.

To se provádí prostřednictvím definuje jednu nebo více tříd ContentTypeDefinition:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

V předchozím příkladu se vytvoří definice typu obsahu pro soubory, které končí *.bar* příponu souboru. Definice typu obsahu je uveden název "panel" a **musí** odvozovat [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Po přidání definice typu obsahu, pak můžete definovat, kdy se má načíst rozšíření jazyka klienta ve třídě jazyk klienta:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Přidání podpory pro LSP jazyk servery není nutné implementovat systém projektu v sadě Visual Studio. Zákazníci můžou otevřít jeden soubor nebo složku v sadě Visual Studio, pokud chcete začít používat služby jazyka. Ve skutečnosti podpora serverů LSP jazyk je navržen pro práci jenom v situacích, otevřít složku nebo soubor. Pokud je implementovaná vlastní projektový systém, nebudou fungovat některé funkce (například nastavení).

## <a name="advanced-features"></a>Pokročilé funkce

### <a name="settings"></a>Nastavení

Podpora pro vlastní nastavení pro konkrétní jazyk serveru je k dispozici, ale je stále probíhá proces jeho vylepšuje. Nastavení jsou specifická pro co server jazyk podporuje a obvykle řídí, jak jazyk serveru generuje data. Například jazyk serveru může mít nastavení pro maximální počet chyb zaznamenaný. Autoři rozšíření byste definovali výchozí hodnotu, která může změnit uživatele pro konkrétní projekty.

Postupujte podle následujících kroků pro přidání podpory pro nastavení rozšíření služeb jazyka LSP:

1. Přidání souboru JSON (například *MockLanguageExtensionSettings.json*) ve vašem projektu, který obsahuje nastavení a jejich výchozí hodnoty. Příklad:

   ```json
   {
    "foo.maxNumberOfProblems": -1
   }
   ```
2. Klikněte pravým tlačítkem na soubor JSON a vyberte **vlastnosti**. Změnit **sestavení** akce "Obsah" a "zahrnout do VSIX' vlastnost na hodnotu true.

3. Implementace oddíly ConfigurationSections a vrátí seznam předpon pro nastavení definované v souboru JSON (v aplikaci Visual Studio Code, to by namapovat na název oddílu konfigurace v souboru package.json):

   ```csharp
   public IEnumerable<string> ConfigurationSections
   {
      get
      {
          yield return "foo";
      }
   }
   ```
4. Soubor .pkgdef přidejte do projektu (Přidat nový textový soubor a změňte příponu souboru .pkgdef). Soubor pkgdef by měl obsahovat tyto informace:

   ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
   ```

5. Klikněte pravým tlačítkem na soubor .pkgdef a vyberte **vlastnosti**. Změnit **sestavení** akce **obsahu** a **zahrnout do VSIX** vlastnost na hodnotu true.

6. Otevřete *source.extension.vsixmanifest* a přidejte prostředek **Asset** kartu:

   ![Upravit prostředek balíčku vspackage](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft.VisualStudio.VsPackage
   * **Zdroj**: soubor v systému souborů
   * **Cesta**: [cesta k vaší *.pkgdef* souborů]

### <a name="user-editing-of-settings-for-a-workspace"></a>Uživatel upravuje nastavení pro pracovní prostor

1. Uživatel otevře pracovní prostor obsahující soubory, které je vlastníkem vašeho serveru.
2. Uživatel přidá soubor v *.vs* složku s názvem *VSWorkspaceSettings.json*.
3. Uživatel přidá řádek do *VSWorkspaceSettings.json* soubor pro třídu setting server poskytuje. Příklad:

   ```json
   {
    "foo.maxNumberOfProblems": 10
   }
   ```
   ### <a name="enabling-diagnostics-tracing"></a>Povolení trasování diagnostiky
   Diagnostické trasování je možné zapnout na výstup všech zpráv mezi klientem a serverem, který může být užitečné při ladění problémů.  Pokud chcete povolit diagnostické trasování, postupujte takto:

4. Otevření nebo vytvoření souboru nastavení pracovního prostoru *VSWorkspaceSettings.json* (viz "Uživatel upravuje nastavení pro pracovní prostor").
5. Přidejte následující řádek v souboru nastavení json:

```json
{
    "foo.trace.server": "Off"
}
```

Existují tři možné hodnoty pro trasovacího podrobnosti:
* "Off": úplně vypnout trasování
* "Zprávy": trasování zapnuté, ale ID názvu a odpovědi pouze metody jsou trasovány.
* "Verbose": trasování zapnuté; zpráva rpc celý trasován.

Pokud je trasování zapnuto obsah se zapisují do souboru v *%temp%\VisualStudio\LSP* adresáře.  Protokol formát pojmenování *[LanguageClientName]-[razítko data a času] log*.  V současné době můžete trasování povoleno pouze pro otevřenou složku.  Otevření jednoho souboru aktivace jazyk serveru nemá žádné diagnostické trasování podpory.

### <a name="custom-messages"></a>Vlastní zprávy

Rozhraní API na místě pro usnadnění předávání zpráv a přijímání zpráv ze serveru jazyka, které nejsou součástí standardní protokol jazyka serveru nejsou k dispozici. Pro zpracování vlastní zprávy, implementovat [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) rozhraní ve třídě jazyk klienta. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) knihovna se používá k přenosu vlastního zpráv mezi jazyk klienta a serveru jazyka. Rozšíření LSP jazyk klienta je stejně jako ostatní rozšíření sady Visual Studio, můžete přidat další funkce, (, které nejsou podporované LSP) do sady Visual Studio (s použitím jiných Visual Studio rozhraní API) v rozšíření prostřednictvím vlastních zpráv.

#### <a name="receiving-custom-messages"></a>Příjem zpráv s vlastní

Chcete-li vlastní zprávy ze serveru pro jazyk, implementovat [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) vlastnost [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) a vrátí objekt, který umí zpracovat vlastní zprávy . Následující příklad:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>Odesílání vlastních zpráv

Chcete-li odeslat vlastní zprávy na language server, implementovat [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) metoda [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Tato metoda vyvolána, když je váš jazyk server spuštěn a připravený pro příjem zpráv. A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) objekt je předán jako parametr, který potom můžete ponechat pro odesílání zpráv do serveru pomocí jazyka [VS StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) rozhraní API. Následující příklad:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {    
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Střední vrstva

Vývojář rozšíření může někdy chcete zachytit LSP zprávy odesílané do a ze serveru pro jazyk. Vývojář rozšíření může například chcete změnit zprávu parametru odeslaného příslušné LSP zprávy nebo upravit výsledky vrácené ze serveru jazyk pro funkci LSP (například dokončování). Pokud je to nezbytné, rozšíření mohou vývojáři MiddleLayer API zachytit LSP zprávy.

Každá zpráva LSP má svůj vlastní střední vrstvu rozhraní pro zachycení. Aby se zachytily určité zprávy, vytvořte třídu, která implementuje rozhraní prostřední vrstva pro tuto zprávu. Pak implementovat [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) rozhraní ve třídě jazyk klienta a vrátit instanci objektu v [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) vlastnost. Následující příklad:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Funkce prostřední vrstva je stále ve vývoji a ještě nejsou úplné.

## <a name="sample-lsp-language-server-extension"></a>Rozšíření ukázky LSP jazyka serveru

Zdrojový kód ukázkové rozšíření pomocí rozhraní API klienta LSP v sadě Visual Studio najdete v tématu ukázky rozšiřitelnosti VSSDK [LSP ukázka](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Nejčastější dotazy

**Chci vytvořit vlastní projekt systém k doplnění LSP jazyk serveru k poskytování bohatších podporovaných funkcích v sadě Visual Studio, jak se mám obrátit o to provedete?**

Podpora jazyka založeného na LSP serverů v sadě Visual Studio využívá [funkce Otevřít složku](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) a je speciálně navržen pro, aby vlastní projektový systém. Můžete vytvářet vlastní projekt systému postupujte podle pokynů [tady](https://github.com/Microsoft/VSProjectSystem), ale některé funkce, jako je například nastavení, nemusí fungovat. Výchozí inicializace logiku pro servery LSP jazyka je a zajistěte tak předání složky, do kořenové složky je aktuálně otevřenou, takže pokud používáte vlastní projektový systém, budete muset poskytnout vlastní logiku během inicializace k zajištění můžete server language správně spusťte.

**Jak přidám podpora ladicího programu?**

Společnost Microsoft poskytuje podporu [běžné ladění protokolu](https://code.visualstudio.com/docs/extensionAPI/api-debugging) v budoucí verzi.

**Pokud VS podporované jazykové služby nainstalovaná (třeba JavaScriptu) již existuje, je možné i nadále nainstalovat rozšíření LSP jazyk serveru, která nabízí další funkce (například linting)?**

Ano, ale ne všechny funkce bude fungovat správně. Konečným cílem pro rozšíření serveru LSP jazyka je umožnit jazykových služeb nativně podporuje Visual Studio. Můžete vytvořit rozšíření, která nabízí další podporu LSP jazyk serverů, ale některé funkce (jako je například technologie IntelliSense) nebudou hladký. Obecně se doporučuje, LSP jazyk serveru rozšíření lze použít k poskytnutí nové prostředí pro jazyk, není rozšíření existující aplikace.

**Kde můžu publikovat Moje dokončené jazyk serveru LSP VSIX?**

Pokyny k Marketplace [tady](walkthrough-publishing-a-visual-studio-extension.md).
