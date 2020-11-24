---
title: Přidání rozšíření protokolu jazykového serveru | Microsoft Docs
description: Naučte se vytvořit rozšíření sady Visual Studio, které integruje jazykový Server na základě protokolu LSP (Language Server Protocol).
ms.custom: SEO-VS-2020
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26f78be8708e61370be3256c8cde481d5c61c89d
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598143"
---
# <a name="add-a-language-server-protocol-extension"></a>Přidání rozšíření protokolu LSP (Language Server Protocol)

Protokol LSP (Language Server Protocol) je běžný protokol ve formě JSON RPC v 2.0, který slouží k poskytování funkcí jazykové služby různým editorům kódu. Pomocí protokolu můžou vývojáři psát jeden jazykový Server, který poskytuje funkce služby jazyka, jako je IntelliSense, diagnostika chyb, najít všechny odkazy a tak dále k různým editorům kódu, které podporují LSP. Jazykové služby v sadě Visual Studio je tradičně možné přidat pomocí TextMate gramatických souborů, které poskytují základní funkce, jako je zvýrazňování syntaxe nebo psaní vlastních jazykových služeb, které používají úplnou sadu rozhraní API rozšíření sady Visual Studio k poskytování rozsáhlejších dat. Díky podpoře poskytovatele LSP v aplikaci Visual Studio je k dispozici třetí možnost.

![Služba protokolu jazykového serveru v aplikaci Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Protokol jazyka serveru

![implementace protokolu jazykového serveru](media/lsp-implementation.png)

Tento článek popisuje, jak vytvořit rozšíření sady Visual Studio, které používá jazykový server založený na LSP. Předpokládá, že už máte vyvinutý jazykový server založený na LSP a chcete ho jenom integrovat do sady Visual Studio.

Pro podporu v rámci sady Visual Studio můžou jazykové servery komunikovat s klientem (Visual Studio) prostřednictvím libovolného přenosového mechanismu založeného na datových proudech, například:

* Standardní vstupní/výstupní proudy
* Pojmenované kanály
* Sokety (pouze TCP)

Účelem LSP a podpory pro IT v aplikaci Visual Studio je připojit jazykové služby, které nejsou součástí produktu Visual Studio. Není určen pro rozšiřování stávajících jazykových služeb (například C#) v aplikaci Visual Studio. Pokud chcete rozšíření stávajících jazyků, přečtěte si příručku k rozšíření jazykové služby (například ["Roslyn" .NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)), nebo se podívejte na téma [rozšíření editoru a jazykových služeb](../extensibility/extending-the-editor-and-language-services.md).

Další informace o samotném protokolu najdete v dokumentaci [zde](https://github.com/Microsoft/language-server-protocol).

Další informace o tom, jak vytvořit ukázkový jazykový Server nebo jak integrovat existující jazykový Server do Visual Studio Code, najdete v dokumentaci [zde](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Funkce podporované protokolem jazykového serveru

Následující tabulky ukazují, které funkce LSP jsou podporovány v aplikaci Visual Studio:

Zpráva | Má podporu v aplikaci Visual Studio
--- | ---
spuštění | ano
inicializované | ano
vypnutí | ano
akci | ano
$/cancelRequest | ano
okno/showMessage | ano
okno/showMessageRequest | ano
okno/LogMessage – | ano
telemetrie/událost |
klient/registerCapability |
klient/unregisterCapability |
pracovní prostor/didChangeConfiguration | ano
pracovní prostor/didChangeWatchedFiles | ano
pracovní prostor nebo symbol | ano
pracovní prostor/executeCommand | ano
pracovní prostor/applyEdit | ano
textDocument/publishDiagnostics | ano
textDocument/didOpen | ano
textDocument/didChange | ano
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | ano
textDocument/didClose | ano
textDocument/dokončení | ano
dokončení/vyřešení | ano
textDocument/najetí myší | ano
textDocument/signatureHelp | ano
textDocument/odkazy | ano
textDocument/documentHighlight | ano
textDocument/documentSymbol | ano
textDocument/formátování | ano
textDocument/rangeFormatting | ano
textDocument/onTypeFormatting |
textDocument/definice | ano
textDocument/codeAction | ano
textDocument/codeLens |
codeLens/vyřešit |
textDocument/documentLink |
documentLink/vyřešit |
textDocument/přejmenovat | ano

## <a name="get-started"></a>Začínáme

> [!NOTE]
> Počínaje verzí Visual Studio 2017 verze 15,8 je podpora pro protokol Common Language Server integrována do sady Visual Studio. Pokud jste vytvořili rozšíření LSP pomocí verze [VSIX klienta serveru jazyka](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) Preview, přestane po upgradu na verzi 15,8 nebo vyšší fungovat. K opětovnému fungování rozšíření LSP bude nutné provést následující kroky:
>
> 1. Odinstalujte VSIX rozhraní Microsoft Visual Studio Language Server Protocol Preview.
>
>    Počínaje verzí 15,8 se při každém provedení upgradu v aplikaci Visual Studio automaticky rozpozná a odebere verze Preview VSIX.
>
> 2. Aktualizujte svůj odkaz na NuGet na nejnovější verzi bez verze Preview pro [balíčky LSP](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Odeberte závislost na VSIX služby Microsoft Visual Studio Language Server Protocol Preview v manifestu VSIX.
>
> 4. Ujistěte se, že VSIX určuje Visual Studio 2017 verze 15,8 Preview 3 jako dolní mez pro cíl instalace.
>
> 5. Proveďte opětné sestavení a nasazení.

### <a name="create-a-vsix-project"></a>Vytvoření projektu VSIX

Pokud chcete vytvořit rozšíření jazykové služby pomocí serveru založeného na LSP, nejdřív se ujistěte, že máte nainstalovanou úlohu **vývoj rozšíření sady Visual Studio** pro vaši instanci vs.

Dále vytvořte nový projekt VSIX tak, že přejdete na **soubor**  >  **Nový projekt**  >  **Visual C#**  >  **rozšíření**  >  **VSIX** Visual C#:

![vytvořit projekt VSIX](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Instalace jazykového serveru a modulu runtime

Ve výchozím nastavení rozšíření vytvořená pro podporu jazykových serverů založených na LSP v aplikaci Visual Studio neobsahují samotné jazykové servery nebo moduly runtime potřebné k jejich spuštění. Vývojáři rozšíření zodpovídají za distribuci jazykových serverů a potřebných modulů runtime. To lze provést několika způsoby:

* Jazykové servery lze vložit do souboru VSIX jako soubory obsahu.
* Vytvořte soubor MSI pro instalaci jazykového serveru a/nebo potřebných modul runtime.
* Poskytněte pokyny na webu Marketplace informující o tom, jak získat moduly runtime a jazykové servery.

### <a name="textmate-grammar-files"></a>Soubory gramatiky TextMate

LSP nezahrnuje specifikaci, jak zadat barvu textu pro jazyky. Pro zajištění vlastní barevného zabarvení pro jazyky v aplikaci Visual Studio můžou vývojáři rozšíření použít soubor gramatiky TextMate. Chcete-li přidat vlastní TextMate gramatiky nebo soubory motivů, postupujte podle následujících kroků:

1. V rámci rozšíření vytvořte složku s názvem "gramatiky" (nebo se může jednat o libovolný název, který zvolíte).

2. Do složky *gramatiky* Zahrňte všechny soubory *\* . tmlanguage*, *\* . plist*, *\* . tmtheme* nebo *\* . JSON* , které byste chtěli použít k vlastnímu zabarvení.

   > [!TIP]
   > Soubor *. tmtheme* definuje, jak se obory mapují na klasifikace sady Visual Studio (pojmenované barevné klíče). Pro doprovodné materiály můžete odkazovat na soubor Global *. tmtheme* v adresáři *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \\ \<SKU> \Common7\IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* .

3. Vytvořte soubor *. pkgdef* a přidejte řádek podobný tomuto:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Pravým tlačítkem myši klikněte na soubory a vyberte **vlastnosti**. Změňte akci **sestavení** na **obsah** a změňte vlastnost **Zahrnout ve vlastnosti VSIX** na **hodnotu true**.

Po dokončení předchozích kroků se složka *gramatik* přidá do instalačního adresáře balíčku jako zdroj úložiště s názvem ' MyLang ' (' MyLang ' je pouze název pro nejednoznačnosti a může to být libovolný jedinečný řetězec). Všechny gramatiky (soubory *. tmlanguage* ) a soubory motivů (soubory *. tmtheme* ) v tomto adresáři se vybírají jako potenciální a nahrazují vestavěné gramatiky, které jsou k dispozici v TextMate. Pokud se deklarované přípony v gramatickém souboru shodují s příponou otevřeného souboru, TextMate se podrobí.

## <a name="create-a-simple-language-client"></a>Vytvoření jednoduchého jazykového klienta

### <a name="main-interface---ilanguageclient"></a>Hlavní rozhraní – [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)

Po vytvoření projektu VSIX přidejte do projektu následující balíčky NuGet:

* [Microsoft. VisualStudio. LanguageServer. Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Když po dokončení předchozích kroků vyberete závislost na balíčku NuGet, balíčky Newtonsoft.Json a StreamJsonRpc se také přidají do vašeho projektu. **Neaktualizujte tyto balíčky, pokud jste si jisti, že tyto nové verze budou nainstalovány ve verzi sady Visual Studio, kterou vaše rozšíření cílí**. Sestavení nebudou součástí VSIX. místo toho budou převzaty z instalačního adresáře sady Visual Studio. Pokud odkazujete na novější verzi sestavení, než jaká je nainstalovaná v počítači uživatele, nebude rozšíření fungovat.

Pak můžete vytvořit novou třídu, která implementuje rozhraní [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true) , což je hlavní rozhraní potřebné pro jazykové klienty, kteří se připojují k serveru jazyka založenému na LSP.

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

Hlavní metody, které je třeba implementovat, jsou [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) a [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017&preserve-view=true) se volá, když Visual Studio načte vaše rozšíření a váš jazykový Server je připravený k zahájení. V této metodě můžete okamžitě vyvolat delegáta [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) k signalizaci, že by měl být jazykový Server spuštěný, nebo můžete provést další logiku a vyvolat [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) později. **Pokud chcete aktivovat svůj jazykový Server, musíte v nějakém okamžiku volat StartAsync.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017&preserve-view=true) je metoda, která se nakonec vyvolala voláním delegáta [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017&preserve-view=true) . Obsahuje logiku ke spuštění jazykového serveru a navázání připojení k němu. Je nutné vrátit objekt připojení, který obsahuje datové proudy pro zápis na server a čtení ze serveru. Všechny výjimky, které jsou zde vyvolány, jsou zachyceny a zobrazeny uživateli prostřednictvím zprávy informačního panelu v aplikaci Visual Studio.

### <a name="activation"></a>Aktivace

Po implementaci třídy klientského klienta budete muset definovat dva atributy pro definování způsobu, jakým se bude načítat do sady Visual Studio, a aktivovat:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio používá [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) ke správě bodů rozšiřitelnosti. Atribut [Export](/dotnet/api/system.componentmodel.composition.exportattribute) označuje aplikaci Visual Studio, že by měla být tato třída vyzvednuta jako rozšiřovací bod a načtena v příslušném čase.

Chcete-li použít MEF, je nutné také definovat MEF jako Asset v manifestu VSIX.

Otevřete návrháře manifestu VSIX a přejděte na kartu **assets (prostředky** ):

![Přidat prostředek MEF](media/lsp-add-asset.png)

Kliknutím na **Nový** vytvořte nový prostředek:

![definovat prostředek MEF](media/lsp-define-asset.png)

* **Zadejte**: Microsoft. VisualStudio. MefComponent
* **Zdroj**: projekt v aktuálním řešení
* **Projekt**: [váš projekt]

### <a name="content-type-definition"></a>Definice typu obsahu

V současné době jediný způsob, jak načíst rozšíření jazyka založeného na LSP, je podle typu obsahu souboru. To znamená, že při definování třídy klientského klienta (která implementuje [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017&preserve-view=true)) budete muset definovat typy souborů, které při otevření způsobí, že se rozšíření načte. Pokud nejsou otevřené žádné soubory, které odpovídají definovanému typu obsahu, nebude rozšíření načteno.

To se provádí pomocí definování jedné nebo více `ContentTypeDefinition` tříd:

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

V předchozím příkladu se vytvoří definice typu obsahu pro soubory, které končí příponou souboru *. bar* . Definice typu obsahu má název "bar" a musí se odvozovat z [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017&preserve-view=true).

Po přidání definice typu obsahu můžete definovat, kdy se má načítat jazykové rozšíření klienta v klientské třídě jazyka:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Přidání podpory pro jazykové servery LSP nevyžaduje, abyste implementovali vlastní systém projektu v aplikaci Visual Studio. Zákazníci mohou otevřít jeden soubor nebo složku v aplikaci Visual Studio, aby mohli začít používat jazykovou službu. Kromě toho je podpora pro jazykové servery LSP navržena tak, aby fungovala pouze v otevřených scénářích složek a souborů. Pokud je implementován vlastní systém projektu, některé funkce (například nastavení) nebudou fungovat.

## <a name="advanced-features"></a>Pokročilé funkce

### <a name="settings"></a>Nastavení

K dispozici je podpora vlastního nastavení pro konkrétní jazyk a server, ale stále probíhá jeho vylepšené zpracování. Nastavení jsou specifická pro to, co podporuje jazykový Server, a obvykle řídí způsob, jakým daný jazykový server posílá data. Například jazykový Server může mít nastavení pro maximální počet hlášených chyb. Autoři rozšíření by definovali výchozí hodnotu, kterou mohou uživatelé změnit pro konkrétní projekty.

Pomocí následujících kroků přidejte podporu pro nastavení do rozšíření služby jazyka LSP:

1. Přidejte soubor JSON (například *MockLanguageExtensionSettings.json*) do projektu, který obsahuje nastavení a jejich výchozí hodnoty. Například:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Klikněte pravým tlačítkem na soubor JSON a vyberte **vlastnosti**. Změňte akci **sestavení** na "obsah" a vlastnost zahrnout do VSIX na **hodnotu true**.

3. Implementujte rozhraní ConfigurationSection a vraťte seznam předpon pro nastavení definovaná v souboru JSON (v Visual Studio Code to se namapuje na název konfiguračního oddílu v package.jsna):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Přidejte do projektu soubor. pkgdef (přidejte nový textový soubor a změňte příponu souboru na. pkgdef). Soubor pkgdef by měl obsahovat tyto informace:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Ukázka:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Klikněte pravým tlačítkem na soubor. pkgdef a vyberte **vlastnosti**. Změňte akci **sestavení** na **obsah** a vlastnost **zahrnout do VSIX** na **hodnotu true**.

6. Otevřete soubor *source. extension. vsixmanifest* a přidejte Asset na kartu **Asset (Asset** ):

   ![Upravit prostředek VSPackage](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft. VisualStudio. VSPackage
   * **Zdroj**: soubor v systému souborů
   * **Cesta**: [cesta k souboru *. pkgdef* ]

### <a name="user-editing-of-settings-for-a-workspace"></a>Úprava nastavení pro pracovní prostor uživatelem

1. Uživatel otevře pracovní prostor obsahující soubory, které váš server vlastní.
2. Uživatel přidá soubor do složky *. vs* s názvem *VSWorkspaceSettings.js*.
3. Uživatel přidá řádek do *VSWorkspaceSettings.jsv* souboru pro nastavení serveru. Například:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Povolit trasování diagnostiky

Trasování diagnostiky lze povolit pro výstup všech zpráv mezi klientem a serverem, což může být užitečné při ladění problémů. Chcete-li povolit trasování diagnostiky, postupujte takto:

1. Otevřete nebo vytvořte soubor nastavení pracovního prostoru *VSWorkspaceSettings.jsv* (viz "Úprava nastavení uživatele pro pracovní prostor").
2. Do souboru JSON nastavení přidejte následující řádek:

```json
{
    "foo.trace.server": "Off"
}
```

Existují tři možné hodnoty pro podrobnost trasování:

* "Off": trasování bylo zcela vypnuto.
* "Messages": trasování je zapnuto, ale je sledován pouze název metody a ID odpovědi.
* Verbose: trasování je zapnuté. celá zpráva RPC je sledována.

Když je trasování zapnuté, obsah se zapisuje do souboru v adresáři *%TEMP%\VisualStudio\LSP* . Protokol se řídí formátem názvů *[LanguageClientName] – [DateTime Stamp]. log*. V současné době je možné trasování povolit pouze pro scénáře otevřené složky. Otevření jednoho souboru pro aktivaci jazykového serveru nemá podporu trasování diagnostiky.

### <a name="custom-messages"></a>Vlastní zprávy

K dispozici jsou rozhraní API pro usnadnění předávání a přijímání zpráv z jazykového serveru, které nejsou součástí protokolu standardního jazykového serveru. Chcete-li zpracovat vlastní zprávy, implementujte rozhraní [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) ve třídě klientského klienta. Knihovna [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) se používá k přenosu vlastních zpráv mezi klientským a jazykovým serverem. Vzhledem k tomu, že rozšíření klientského klienta LSP je stejné jako jiné rozšíření sady Visual Studio, můžete se rozhodnout přidat další funkce (které poskytovatel LSP nepodporuje) do sady Visual Studio (pomocí jiných rozhraní API sady Visual Studio) ve vašem rozšíření prostřednictvím vlastních zpráv.

#### <a name="receive-custom-messages"></a>Přijímání vlastních zpráv

Chcete-li přijímat vlastní zprávy z jazykového serveru, implementujte vlastnost [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017&preserve-view=true) v [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) a vraťte objekt, který ví, jak zpracovávat vlastní zprávy. Příklad:

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

Chcete-li odesílat vlastní zprávy na daný jazykový Server, Implementujte metodu [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017&preserve-view=true) na [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true). Tato metoda je vyvolána, když je váš jazykový Server spuštěný a je připravený přijímat zprávy. Objekt [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) se předává jako parametr, který pak můžete dál posílat zprávy na daný jazykový Server pomocí rozhraní API sady [vs-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) . Příklad:

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

### <a name="middle-layer"></a>Prostřední vrstva

V některých případech může vývojář rozšíření zachytávání zpráv LSP odesílaných a přijatých z daného jazykového serveru. Například vývojář rozšíření může chtít změnit parametr zprávy odeslaný pro konkrétní zprávu LSP nebo upravit výsledky vrácené z jazykového serveru pro funkci LSP (například dokončení). Pokud je to nezbytné, vývojáři rozšíření můžou k zachycení zpráv LSP použít rozhraní MiddleLayer API.

Každá zpráva LSP má své vlastní rozhraní střední vrstvy pro zachycení. Chcete-li zachytit konkrétní zprávu, vytvořte třídu, která implementuje rozhraní střední vrstvy pro danou zprávu. Potom implementujte rozhraní [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017&preserve-view=true) v klientské třídě jazyka a vraťte instanci objektu do vlastnosti [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017&preserve-view=true) . Příklad:

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

Funkce prostřední vrstvy je stále ve vývoji a ještě není vyčerpávající.

## <a name="sample-lsp-language-server-extension"></a>Ukázka rozšíření serveru LSP Language Server

Pokud chcete zobrazit zdrojový kód ukázkového rozšíření pomocí rozhraní API klienta LSP v aplikaci Visual Studio, přečtěte si ukázku VSSDK-rozšiřitelnost-Samples [LSP](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Nejčastější dotazy

**Chci vytvořit vlastní systém projektu, který doplňuje svůj jazykový Server LSP, aby poskytoval širší podporu funkcí v aplikaci Visual Studio, jak se dá to udělat?**

Podpora pro jazykové servery založené na LSP v aplikaci Visual Studio se spoléhá na [funkci otevřené složky](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) a je navržena tak, aby nevyžadovala vlastní systém projektu. Vlastní systém projektu můžete vytvořit [podle pokynů,](https://github.com/Microsoft/VSProjectSystem)ale některé funkce, například nastavení, nemusí fungovat. Výchozí inicializační logika pro jazykové servery LSP se předává do umístění kořenové složky aktuálně otevřené složky, takže pokud používáte vlastní systém projektu, možná budete muset během inicializace zadat vlastní logiku, abyste zajistili, že se Váš jazykový Server může správně spustit.

**Návody přidat podporu ladicího programu?**

V budoucí verzi budeme poskytovat podporu pro [Common Debugging Protocol](https://code.visualstudio.com/docs/extensionAPI/api-debugging) .

**Pokud už je nainstalovaná podporovaná jazyková služba VS (například JavaScript), můžu I přesto nainstalovat rozšíření jazykové Server LSP, které nabízí další funkce (například linting)?**

Ano, ale ne všechny funkce budou fungovat správně. Hlavním cílem rozšíření pro jazykové servery LSP je povolit jazykové služby, které Visual Studio netivně podporuje. Můžete vytvořit rozšíření, která nabízejí další podporu pomocí jazykových serverů LSP, ale některé funkce (například IntelliSense) nebudou mít hladké prostředí. Obecně se doporučuje, aby se rozšíření pro jazykové servery LSP používala k poskytování nových jazyků a nerozšiřují stávající.

**Kde můžu publikovat dokončený VSIX jazykového serveru LSP?**

[Tady se můžete](walkthrough-publishing-a-visual-studio-extension.md)podívat na pokyny pro Marketplace.

## <a name="see-also"></a>Viz také

- [Přidat podporu editoru sady Visual Studio pro jiné jazyky](../ide/adding-visual-studio-editor-support-for-other-languages.md)
