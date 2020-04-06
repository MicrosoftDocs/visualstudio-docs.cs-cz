---
title: Přidání rozšíření language server protocol | Dokumenty společnosti Microsoft
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740231"
---
# <a name="add-a-language-server-protocol-extension"></a>Přidání rozšíření protokolu LSP (Language Server Protocol)

Protokol LSP (Language Server Protocol) je běžný protokol ve formě protokolu JSON RPC verze 2.0, který se používá k poskytování funkcí jazykových služeb různým editorům kódu. Pomocí protokolu mohou vývojáři napsat jeden jazykový server, který poskytuje funkce jazykových služeb, jako je IntelliSense, diagnostika chyb, hledání všech odkazů a tak dále na různé editory kódu, které podporují lsp. Tradičně jazykové služby v sadě Visual Studio lze přidat pomocí textmate gramatické soubory poskytovat základní funkce, jako je zvýraznění syntaxe nebo psaní vlastních jazykových služeb, které používají úplnou sadu rozhraní API rozšiřitelnosti sady Visual Studio poskytovat bohatší data. S podporou visual studio pro LSP, je tu třetí možnost.

![služba protokolu jazykového serveru v sadě Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protokol jazyka serveru

![implementace protokolu jazykového serveru](media/lsp-implementation.png)

Tento článek popisuje, jak vytvořit rozšíření sady Visual Studio, které používá jazykový server založený na lsp. Předpokládá, že jste již vyvinuli jazykový server založený na LSP a chcete jej integrovat do sady Visual Studio.

Pro podporu v rámci sady Visual Studio mohou jazykové servery komunikovat s klientem (Visual Studio) prostřednictvím libovolného přenosového mechanismu založeného na datovém proudu, například:

* Standardní vstupní a výstupní datové proudy
* Pojmenované kanály
* Sokety (pouze tcp)

Záměrem LSP a podporu pro něj v sadě Visual Studio je na palubě jazykové služby, které nejsou součástí produktu Sady Visual Studio. Není určena k rozšíření existující jazykové služby (například C#) v sadě Visual Studio. Chcete-li rozšířit stávající jazyky, podívejte se do průvodce rozšiřitelností jazykové služby (například ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) nebo v [tématu Rozšíření editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md).

Další informace o samotném protokolu naleznete v dokumentaci [zde](https://github.com/Microsoft/language-server-protocol).

Další informace o vytvoření ukázkového jazykového serveru nebo o integraci existujícího jazykového serveru do kódu sady Visual Studio naleznete v dokumentaci [zde](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Funkce podporované protokolem Language Server Protocol

V následujících tabulkách jsou uvedeny funkce LSP podporované v sadě Visual Studio:

Zpráva | Má podporu v sadě Visual Studio
--- | ---
Inicializovat | ano
Inicializován | ano
vypnutí | ano
Ukončit | ano
$/cancelPožadavek | ano
okno/showMessage | ano
okno/showMessageRequest | ano
okno/logMessage | ano
telemetrie/událost |
klient/registerSchopnost |
klient/unregisterSchopnost |
workspace/didChangeConfiguration | ano
pracovní prostor/didChangeWatchedFiles | ano
pracovní prostor/symbol | ano
workspace/executeCommand | ano
pracovní prostor/applyEditovat | ano
textDocument/publishDiagnostics | ano
textDokument/didOpen | ano
textDokument/didChange | ano
textDokument/willSave |
textDocument/willSaveWaitUntil |
textDokument/didSave | ano
textDocument/didClose textDocument/didClose textDocument/didClose textDocument | ano
textDokument/dokončení | ano
dokončení/vyřešení | ano
textDokument/najetí přes | ano
textDokument/podpisNápověda | ano
textDokument/odkazy | ano
textDokument/documentHighlight | ano
textDocument/documentSymbol | ano
textDokument/formátování | ano
textDokument/rangeFormátování | ano
textDocument/onTypeForformátování |
textDokument/definice | ano
textDokument/codeAction | ano
textDokument/codeLens |
codeLens/resolve |
textDokument/dokumentOdkaz |
documentLink/resolve |
textDokument/přejmenování | ano

## <a name="get-started"></a>Začínáme

> [!NOTE]
> Počínaje Visual Studio 2017 verze 15.8, podpora pro společný protokol Language Server Protocol je integrován do sady Visual Studio. Pokud jste vytvořili rozšíření LSP pomocí verze Preview [Language Server Client VSIX,](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) přestanou fungovat po upgradu na verzi 15.8 nebo vyšší. Budete muset udělat následující kroky, aby vaše Rozšíření LSP znovu zpracovala:
>
> 1. Odinstalujte protokol VSIX protokolu Microsoft Visual Studio Language Server Protocol VSIX.
>
>    Počínaje verzí 15.8 se při každém upgradu v sadě Visual Studio automaticky rozpozná a odebere náhled VSIX.
>
> 2. Aktualizujte odkaz Nuget na nejnovější verzi bez náhledu pro [balíčky LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Odeberte závislost na microsoft visual studio language server protokol náhled u verze VSIX v manifestu VSIX.
>
> 4. Ujistěte se, že váš VSIX určuje Visual Studio 2017 verze 15.8 Náhled 3 jako dolní mez pro cíl instalace.
>
> 5. Proveďte opětné sestavení a nasazení.

### <a name="create-a-vsix-project"></a>Vytvoření projektu VSIX

Chcete-li vytvořit rozšíření služby jazyka pomocí jazykového serveru založeného na LSP, nejprve se ujistěte, že máte nainstalovanou **pracovní zátěž pro vývoj rozšíření Visual Studio** pro vaši instanci VS.

Dále vytvořte nový projekt VSIX přechodem na **soubor nového** > **projektu** > **Visual C#** > **Rozšiřitelnost** > **vsix projektu**:

![vytvořit projekt vsix](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Jazykový server a instalace za běhu

Ve výchozím nastavení rozšíření vytvořená pro podporu jazykových serverů založených na standardu LSP v sadě Visual Studio neobsahují samotné jazykové servery ani dobu runmu potřebnou k jejich spuštění. Vývojáři rozšíření jsou zodpovědní za distribuci jazykových serverů a potřebných runtimesů. Existuje několik způsobů, jak to udělat:

* Jazykové servery mohou být vloženy do VSIX jako soubory obsahu.
* Vytvořte MSI pro instalaci jazykového serveru nebo potřebných runtimes.
* Poskytněte pokyny na marketplace, kde uživatele informujte o tom, jak získat runtimes a jazykové servery.

### <a name="textmate-grammar-files"></a>Textové soubory gramatiky TextMate

LSP neobsahuje specifikaci, jak poskytnout vybarvení textu pro jazyky. Chcete-li poskytnout vlastní vybarvení pro jazyky v sadě Visual Studio, mohou vývojáři rozšíření použít soubor gramatiky TextMate. Chcete-li přidat vlastní gramatiku TextMate nebo soubory motivů, postupujte takto:

1. Vytvořte složku s názvem "Gramatiky" uvnitř rozšíření (nebo to může být bez ohledu na název, který zvolíte).

2. Do složky *Gramatiky* zahrňte všechny * \*soubory .tmlanguage*, * \*.plist*, * \*.tmtheme*nebo * \*.json,* které poskytují vlastní vybarvení.

   > [!TIP]
   > Soubor *Tmtheme* definuje, jak se obory mapují na klasifikace sady Visual Studio (pojmenované barevné klávesy). Chcete-li podat pokyny, můžete odkazovat na globální soubor *Tmtheme* v adresáři *%ProgramFiles(x86)%\Microsoft\\\<Visual Studio>\\ \<sku>\Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg.*

3. Vytvořte soubor *.pkgdef* a přidejte řádek podobný tomuto:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Klepněte pravým tlačítkem myši na soubory a vyberte **příkaz Vlastnosti**. Změňte akci **Sestavení** na **obsah** a změňte vlastnost **Zahrnout do VSIX** na **hodnotu true**.

Po dokončení předchozích kroků je složka *Gramatiky přidána* do instalačního adresáře balíčku jako zdroj úložiště s názvem "MyLang" ("MyLang" je pouze název pro rozdvojení a může být libovolný jedinečný řetězec). Všechny gramatiky (*.tmlanguage* soubory) a téma soubory (*.tmtheme* soubory) v tomto adresáři jsou zvedl jako potenciál a nahrazují vestavěný gramatiky dodaný s TextMate. Pokud deklarované přípony souboru gramatiky odpovídají příponě otevřeného souboru, vstoupí do ní TextMate.

## <a name="create-a-simple-language-client"></a>Vytvoření jednoduchého jazykového klienta

### <a name="main-interface---ilanguageclient"></a>Hlavní rozhraní - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Po vytvoření projektu VSIX přidejte do projektu následující balíčky NuGet:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Když budete mít závislost na balíčku NuGet po dokončení předchozích kroků, Newtonsoft.Json a StreamJsonRpc balíčky jsou přidány do projektu také. **Neaktualizujte tyto balíčky, pokud si nejste jisti, že tyto nové verze budou nainstalovány ve verzi sady Visual Studio, na kterou vaše rozšíření cílí**. Sestavení nebudou zahrnuta do vašeho VSIX; místo toho budou vyzvednuty z instalačního adresáře sady Visual Studio. Pokud odkazujete na novější verzi sestavení, než jaká je nainstalována v počítači uživatele, rozšíření nebude fungovat.

Potom můžete vytvořit novou třídu, která implementuje rozhraní [ILanguageClient,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) což je hlavní rozhraní potřebné pro jazykové klienty, kteří se připojují k jazykovému serveru založenému na lsp.

Následuje ukázka:

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

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Hlavní metody, které je třeba implementovat, jsou [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) a [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) je volána, když Visual Studio načetl orozšíření a váš jazykový server je připraven ke spuštění. V této metodě můžete okamžitě vyvolat [delegáta StartAsync,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) který signalizuje, že jazykový server by měl být spuštěn, nebo můžete provést další logiku a vyvolat [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) později. **Chcete-li aktivovat jazykový server, musíte v určitém okamžiku zavolat StartAsync.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) je metoda, která byla nakonec vyvolána voláním [delegáta StartAsync.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) Obsahuje logiku pro spuštění jazykového serveru a navázání připojení k němu. Musí být vrácen objekt připojení, který obsahuje datové proudy pro zápis na server a čtení ze serveru. Všechny výjimky, které jsou zde vyvolány, jsou zachyceny a zobrazeny uživateli prostřednictvím zprávy InfoBar v sadě Visual Studio.

### <a name="activation"></a>Aktivace

Jakmile je vaše třída klienta jazyka implementována, budete muset definovat dva atributy pro tuto třídu definovat, jak bude načten a aktivován:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio používá [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Rozšiřitelnost Framework) ke správě jeho body rozšiřitelnosti. Export [atribut](/dotnet/api/system.componentmodel.composition.exportattribute) označuje Visual Studio, že tato třída by měla být vyzvednuta jako rozšiřující bod a načtena ve vhodnou dobu.

Chcete-li použít MEF, musíte také definovat MEF jako prostředek v manifestu VSIX.

Otevřete návrháře manifestů VSIX a přejděte na kartu **Datové zdroje:**

![přidání datového zdroje MEF](media/lsp-add-asset.png)

Chcete-li vytvořit nový datový zdroj, klepněte na **tlačítko Nový:**

![definovat majetek MEF](media/lsp-define-asset.png)

* **Typ**: Microsoft.VisualStudio.MefComponent
* **Zdroj**: Projekt v aktuálním řešení
* **Projekt**: [Váš projekt]

### <a name="content-type-definition"></a>Definice typu obsahu

V současné době je jediným způsobem, jak načíst rozšíření jazykového serveru založeného na lsp, typ obsahu souboru. To znamená při definování třídy klienta jazyka (který implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), budete muset definovat typy souborů, které při otevření způsobí, že rozšíření načíst. Pokud nejsou otevřeny žádné soubory, které odpovídají vašemu definovanému typu obsahu, rozšíření se nenačte.

To se provádí definováním `ContentTypeDefinition` jedné nebo více tříd:

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

V předchozím příkladu je vytvořena definice typu obsahu pro soubory, které končí příponou souboru *.bar.* Definice typu obsahu je uveden název "bar" a musí být odvozen a [codeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Po přidání definice typu obsahu můžete definovat, kdy se má načíst rozšíření klienta jazyka ve třídě klienta jazyka:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Přidání podpory pro jazykové servery LSP nevyžaduje implementaci vlastního projektového systému v sadě Visual Studio. Zákazníci mohou otevřít jeden soubor nebo složku v sadě Visual Studio a začít používat jazykovou službu. Ve skutečnosti je podpora jazykových serverů LSP navržena tak, aby fungovala pouze ve scénářích otevřených složek nebo souborů. Pokud je implementován vlastní projektový systém, některé funkce (například nastavení) nebudou fungovat.

## <a name="advanced-features"></a>Pokročilé funkce

### <a name="settings"></a>Nastavení

Podpora pro vlastní nastavení specifické pro jazyk-server je k dispozici, ale je stále v procesu zlepšování. Nastavení jsou specifická pro to, co jazykový server podporuje, a obvykle řídí způsob, jakým jazykový server vydává data. Jazykový server může mít například nastavení maximálního počtu hlášených chyb. Autoři rozšíření by definovali výchozí hodnotu, kterou mohou uživatelé změnit pro konkrétní projekty.

Chcete-li přidat podporu pro nastavení do rozšíření služby jazyka LSP, postupujte takto:

1. Přidejte do projektu soubor JSON (například *MockLanguageExtensionSettings.json),* který obsahuje nastavení a jejich výchozí hodnoty. Například:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Klikněte pravým tlačítkem myši na soubor JSON a vyberte **příkaz Vlastnosti**. Změňte **akci Sestavení** na "Obsah" a vlastnost "Zahrnout do VSIX" na **true**.

3. Implementujte ConfigurationSections a vraťte seznam předpon pro nastavení definovaná v souboru JSON (v kódu sady Visual Studio by se to mapovalo na název oddílu konfigurace v souboru package.json):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Přidejte soubor .pkgdef do projektu (přidejte nový textový soubor a změňte příponu souboru na .pkgdef). Soubor pkgdef by měl obsahovat tyto informace:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Ukázka:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Klikněte pravým tlačítkem myši na soubor .pkgdef a vyberte **příkaz Vlastnosti**. Změňte akci **Sestavení** na **obsah** a vlastnost **Zahrnout do VSIX** na **true**.

6. Otevřete soubor *source.extension.vsixmanifest* a přidejte datový zdroj na kartu **Datový zdroj:**

   ![upravit datový zdroj vspackage](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft.VisualStudio.VsPackage
   * **Zdroj**: Soubor v souborovém systému
   * **Cesta**: [Cesta k souboru *.pkgdef]*

### <a name="user-editing-of-settings-for-a-workspace"></a>Uživatelské úpravy nastavení pracovního prostoru

1. Uživatel otevře pracovní prostor obsahující soubory, které server vlastní.
2. Uživatel přidá soubor do složky *.vs* s názvem *VSWorkspaceSettings.json*.
3. Uživatel přidá řádek do souboru *VSWorkspaceSettings.json* pro nastavení, které server poskytuje. Například:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Povolit trasování diagnostiky

Sledování diagnostiky lze povolit pro výstup všech zpráv mezi klientem a serverem, což může být užitečné při ladění problémů. Chcete-li povolit diagnostické trasování, postupujte takto:

1. Otevřete nebo vytvořte soubor nastavení pracovního prostoru *VSWorkspaceSettings.json* (viz "Úpravy nastavení pracovního prostoru uživatelem").
2. Do souboru json nastavení přidejte následující řádek:

```json
{
    "foo.trace.server": "Off"
}
```

Existují tři možné hodnoty pro podrobnost trasování:

* "Vypnuto": trasování bylo zcela vypnuto
* "Zprávy": je zapnuto trasování, ale jsou sledovány pouze názvy metod a ID odpovědi.
* "Verbose": sledování zapnuto; je sledována celá zpráva rpc.

Je-li trasování zapnuto, je obsah zapsán do souboru v adresáři *%temp%\VisualStudio\LSP.* Protokol následuje za formátem pojmenování *[LanguageClientName]-[Datetime Stamp].log*. V současné době lze trasování povolit pouze pro scénáře otevřených složek. Otevření jednoho souboru pro aktivaci jazykového serveru nemá podporu pro sledování diagnostiky.

### <a name="custom-messages"></a>Vlastní zprávy

Existují rozhraní API pro usnadnění předávání zpráv a přijímání zpráv z jazykového serveru, které nejsou součástí standardního protokolu language server. Chcete-li zpracovat vlastní zprávy, implementujte rozhraní [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) ve třídě klienta jazyka. [Knihovna VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) se používá k přenosu vlastních zpráv mezi klientem jazyka a jazykovým serverem. Vzhledem k tomu, že vaše rozšíření klienta jazyka LSP je stejně jako jakékoli jiné rozšíření sady Visual Studio, můžete se rozhodnout přidat další funkce (které lsp) do sady Visual Studio (pomocí jiných rozhraní API sady Visual Studio) v rozšíření prostřednictvím vlastních zpráv.

#### <a name="receive-custom-messages"></a>Přijímání vlastních zpráv

Chcete-li přijímat vlastní zprávy z jazykového serveru, implementujte vlastnost [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) na [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) a vraťte objekt, který ví, jak zpracovat vlastní zprávy. Příklad níže:

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

#### <a name="send-custom-messages"></a>Odesílání vlastních zpráv

Chcete-li odeslat vlastní zprávy na jazykový server, implementujte metodu [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) na [iLanguageClientCustomCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Tato metoda je vyvolána při spuštění jazykového serveru a připraven přijímat zprávy. A [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) objekt je předán jako parametr, který pak můžete ponechat odeslat zprávy na jazykový server pomocí [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) ROZHRANÍ API. Příklad níže:

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

V některých jazycích může vývojář rozšíření chtít zachytit zprávy LSP odeslané a přijaté z jazykového serveru. Vývojář rozšíření může například chtít změnit parametr zprávy odeslaný pro konkrétní zprávu LSP nebo upravit výsledky vrácené ze serveru jazyka pro funkci LSP (například dokončení). Když je to nutné, vývojáři rozšíření můžete použít MiddleLayer API zachytit zprávy LSP.

Každá zpráva LSP má vlastní rozhraní střední vrstvy pro zachycení. Chcete-li zachytit konkrétní zprávu, vytvořte třídu, která implementuje rozhraní střední vrstvy pro tuto zprávu. Potom implementujte rozhraní [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) ve třídě klienta jazyka a vraťte instanci objektu ve vlastnosti [MiddleLayer.](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Příklad níže:

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

Funkce střední vrstvy je stále ve vývoji a ještě není komplexní.

## <a name="sample-lsp-language-server-extension"></a>Ukázkové rozšíření jazykového serveru LSP

Zdrojový kód ukázkového rozšíření pomocí rozhraní API klienta LSP v sadě Visual Studio naleznete v tématu Ukázka [LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol)v souboru VSDK-Extensibility-Samples .

## <a name="faq"></a>Nejčastější dotazy

**Chtěl bych vytvořit vlastní projektový systém, který doplní můj jazykový server LSP a poskytne bohatší podporu funkcí v sadě Visual Studio, jak to mám udělat?**

Podpora jazykových serverů založených na lsp v sadě Visual Studio závisí na [funkci otevřené složky](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) a je navržena tak, aby nevyžadovala vlastní projektový systém. Můžete vytvořit vlastní systém projektu podle pokynů [zde](https://github.com/Microsoft/VSProjectSystem), ale některé funkce, jako je například nastavení, nemusí fungovat. Výchozí logika inicializace jazykových serverů LSP je předat v umístění kořenové složky právě otevřené složky, takže pokud používáte vlastní systém projektu, bude pravděpodobně nutné poskytnout vlastní logiku během inicializace, aby bylo zajištěno, že se jazykový server může správně spustit.

**Jak přidám podporu ladicího programu?**

Budeme poskytovat podporu pro [společný protokol ladění](https://code.visualstudio.com/docs/extensionAPI/api-debugging) v budoucí verzi.

**Pokud již existuje nainstalovaná jazyková služba podporovaná VS (například JavaScript), mohu stále nainstalovat rozšíření jazykového serveru LSP, které nabízí další funkce (například linting)?**

Ano, ale ne všechny funkce budou fungovat správně. Konečným cílem rozšíření jazykového serveru LSP je povolit jazykové služby, které nejsou nativně podporovány visual studio. Můžete vytvořit rozšíření, která nabízejí další podporu pomocí jazykových serverů LSP, ale některé funkce (například Technologie IntelliSense) nebudou bezproblémovým prostředím. Obecně se doporučuje, aby rozšíření jazykového serveru LSP byla použita pro poskytování nových jazykových prostředí, nikoli k rozšíření stávajících.

**Kde mohu publikovat vyplněný jazykový server LSP VSIX?**

Pokyny k Marketplace [najdete zde](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Viz také

- [Přidání podpory editoru Visual Studia pro jiné jazyky](../ide/adding-visual-studio-editor-support-for-other-languages.md)
