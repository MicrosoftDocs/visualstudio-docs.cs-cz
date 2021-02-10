---
title: Vytvoření editoru těla protokolu HTTP pro test výkonnosti webu
description: Naučte se, jak vytvořit vlastní Editor obsahu, který umožňuje upravit obsah textu řetězce nebo binární obsah textu žádosti webové služby.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: e096333d66fffd233bfb4b9de7f40e18f1277846
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966731"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Postupy: Vytvoření vlastního editoru těla protokolu HTTP pro Editor testu výkonnosti webu

Můžete vytvořit vlastní Editor obsahu, který umožňuje upravit obsah textu řetězce nebo binární obsah textu žádosti webové služby, například SOAP, REST, ASMX, WCF, RIA a další typy požadavků webové služby.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Tyto typy editorů můžete implementovat:

- **Editor obsahu řetězce** To je implementováno pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> rozhraní.

- **Editor binárních obsahu** To je implementováno pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní.

Tato rozhraní jsou obsažena v <xref:Microsoft.VisualStudio.TestTools.WebTesting> oboru názvů.

## <a name="create-a-windows-control-library-project"></a>Vytvořit projekt knihovny ovládacích prvků systému Windows

1. V aplikaci Visual Studio vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** . Pojmenujte projekt **MessageEditors**.

   Projekt je přidán do nového řešení a <xref:System.Windows.Forms.UserControl> s názvem *UserControl1.cs* je prezentována v návrháři.

1. Z **panelu nástrojů** v kategorii **běžné ovládací prvky** přetáhněte na <xref:System.Windows.Forms.RichTextBox> povrch UserControl1.

1. V pravém ![ horním rohu ovládacího prvku zvolte akci značky akce (glyf inteligentních značek ](../test/media/vs_winformsmttagglyph.gif) ) <xref:System.Windows.Forms.RichTextBox> a pak vyberte a **ukotvěte v nadřazeném kontejneru**.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt knihovny model Windows Forms a vyberte **vlastnosti**.

1. Ve **vlastnostech** vyberte kartu **aplikace** .

1. V rozevíracím seznamu **cílové rozhraní** vyberte .NET Framework 4 (nebo novější).

1. Zobrazí se dialogové okno **změnit cílovou architekturu** .

1. Vyberte **Ano**.

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel **odkazy** a vyberte možnost **Přidat odkaz**.

1. Zobrazí se dialogové okno **Přidat odkaz** .

1. Vyberte. Karta **net** , přejděte dolů a vyberte **Microsoft. VisualStudio. QualityTools. WebTestFramework** a pak zvolte **OK**.

1. Pokud **Návrhář zobrazení** není ještě otevřený, klikněte v **Průzkumník řešení** pravým tlačítkem myši na **UserControl1.cs** a pak vyberte **zobrazit Návrhář**.

1. Na návrhové ploše klikněte pravým tlačítkem myši a vyberte možnost **Zobrazit kód**.

1. Volitelné Změňte název třídy a konstruktoru z UserControl1 na smysluplný název, například MessageEditorControl:

    > [!NOTE]
    > Ukázka používá MessageEditorControl.

    ```csharp
    namespace MessageEditors
    {
        public partial class MessageEditorControl : UserControl
        {
            public MessageEditorControl()
            {
                InitializeComponent();
            }
        }
    }
    ```

1. Přidejte následující vlastnosti, abyste umožnili získání a nastavení textu v RichTextBox1. <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>Rozhraní bude používat EditString a <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> bude používat EditByteArray:

    ```csharp
    public String EditString
    {
       get
       {
           return this.richTextBox1.Text;
       }
       set
       {
           this.richTextBox1.Text = value;
       }
    }

    public byte[] EditByteArray
    {
       get
       {
           return System.Convert.FromBase64String(richTextBox1.Text);
       }
       set
       {
           richTextBox1.Text = System.Convert.ToBase64String(value, 0, value.Length);
       }
    }
    ```

## <a name="add-a-class-to-the-windows-control-library-project"></a>Přidat třídu do projektu knihovny ovládacích prvků systému Windows

Přidejte do projektu třídu. Použije se k implementaci <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní a.

**Přehled kódu v tomto postupu**

MessageEditorControl <xref:System.Windows.Forms.UserControl> , který byl vytvořen v předchozím postupu, je vytvořena instance jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Instance messageEditorControl je hostována v dialogovém okně modulu plug-in, který je vytvořen <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> metodou. Kromě toho se messageEditorControl <xref:System.Windows.Forms.RichTextBox> naplní obsahem v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> . Vytvoření modulu plug-in však nelze provést, pokud se <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> nevrátí `true` . V případě tohoto editoru <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> vrátí, `true` Pokud <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> obsahuje "XML".

Při úpravách textu řetězce je dokončena a uživatel klikne na **tlačítko OK** v dialogovém okně modul plug-in, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> je volána k získání upravovaného textu jako řetězce a aktualizaci **těla řetězce** v požadavku v editoru výkonu webového testu.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Vytvoření třídy a implementace rozhraní IStringHttpBodyEditorPlugin

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt knihovny ovládacích prvků model Windows Forms a vyberte možnost **Přidat novou položku**.

   Zobrazí se dialogové okno **Přidat novou položku**.

2. Vyberte **třídu**.

3. Do textového pole **název** zadejte smysluplný název třídy, například `MessageEditorPlugins` .

4. Klikněte na tlačítko **Přidat**.

   Class1 se přidá do projektu a zobrazí se v editoru kódu.

5. V editoru kódu přidejte následující `using` příkaz:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Vložte následující kód pro implementaci rozhraní:

    ```csharp
    /// <summary>
    /// Editor for generic text based hierarchical messages such as XML and JSON.
    /// </summary>
    public class XmlMessageEditor : IStringHttpBodyEditorPlugin
    {
        public XmlMessageEditor()
        {
        }

        /// <summary>
        /// Determine if this plugin supports the content type.
        /// </summary>
        /// <param name="contentType">The content type to test.</param>
        /// <returns>Returns true if the plugin supports the specified content type.</returns>
        public bool SupportsContentType(string contentType)
        {
            return contentType.ToLower().Contains("xml");
        }

        /// <summary>
        /// Create a UserControl to edit the specified bytes.
        /// This control will be hosted in the
        /// plugin dialog which provides OK and Cancel buttons.
        /// </summary>
        /// <param name="contentType">The content type of the BinaryHttpBody.</param>
        /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
        /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
        public object CreateEditor(string contentType, string initialValue)
        {
            messageEditorControl = new MessageEditorControl();
            messageEditorControl.EditString = initialValue;
            return this.messageEditorControl;
        }

        /// <summary>
        /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
        /// </summary>
        public string GetNewValue()
        {
            return messageEditorControl.EditString;
        }

        private MessageEditorControl messageEditorControl;
    }
    ```

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Přidat IBinaryHttpBodyEditorPlugin do třídy

Implementujte rozhraní <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Přehled kódu v tomto postupu**

Implementace kódu pro <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní je podobná, jak je <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> popsáno v předchozím postupu. Binární verze však používá pole bajtů pro zpracování binárních dat namísto řetězce.

MessageEditorControl <xref:System.Windows.Forms.UserControl> vytvořená v prvním postupu je vytvořena instance jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Instance messageEditorControl je hostována v dialogovém okně modulu plug-in, který je vytvořen <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> metodou. Kromě toho se messageEditorControl <xref:System.Windows.Forms.RichTextBox> naplní obsahem v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> . Vytvoření modulu plug-in však nelze provést, pokud se <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> nevrátí `true` . V případě tohoto editoru <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> vrátí, `true` Pokud <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> obsahuje "msbin1".

Při úpravách textu řetězce je dokončena a uživatel klikne na **tlačítko OK** v dialogovém okně modul plug-in, <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> je volána k získání upravovaného textu jako řetězce a aktualizaci **BinaryHttpBody. data** v žádosti v editoru výkonu webového testu.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Přidání IBinaryHttpBodyEditorPlugin do třídy

- Napište nebo zkopírujte následující kód v rámci třídy XmlMessageEditor přidané v předchozím postupu pro vytvoření instance třídy Msbin1MessageEditor z <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní a implementaci požadovaných metod:

    ```csharp
    /// <summary>
        /// Editor for MSBin1 content type (WCF messages)
        /// </summary>
        public class Msbin1MessageEditor : IBinaryHttpBodyEditorPlugin
        {
            /// <summary>
            ///
            /// </summary>
            public Msbin1MessageEditor()
            {
            }

            /// <summary>
            /// Determine if this plugin supports a content type.
            /// </summary>
            /// <param name="contentType">The content type to test.</param>
            /// <returns>Returns true if the plugin supports the specified content type.</returns>
            public bool SupportsContentType(string contentType)
            {
                return contentType.ToLower().Contains("msbin1");
            }

            /// <summary>
            /// Create a UserControl to edit the specified bytes. This control will be hosted in the
            /// plugin dialog which provides OK and Cancel buttons.
            /// </summary>
            /// <param name="contentType">The content type of the BinaryHttpBody.</param>
            /// <param name="initialValue">The bytes to edit. The bytes are the payload of a BinaryHttpBody.</param>
            /// <returns>A UserControl capable of displaying and editing the byte array value of the specified content type.</returns>
            public object CreateEditor(string contentType, byte[] initialValue)
            {
                messageEditorControl = new MessageEditorControl();
                messageEditorControl.EditByteArray = initialValue;
                return messageEditorControl;
            }

            /// <summary>
            /// Gets the edited bytes after the OK button is clicked on the plugin dialog.
            /// </summary>
            public byte[] GetNewValue()
            {
                return messageEditorControl.EditByteArray;
            }

            private MessageEditorControl messageEditorControl;
            private object originalMessage;
        }
    ```

## <a name="build-and-deploy-the-plug-ins"></a>Sestavování a nasazování modulů plug-in

1. V nabídce **sestavení** klikněte na příkaz **sestavit \<Windows Form Control Library project name>**.

2. Zavřete všechny instance aplikace Visual Studio.

   > [!NOTE]
   > Zavřením sady Visual Studio se ujistěte, že soubor *. dll* není uzamčený předtím, než se pokusíte o jeho zkopírování.

3. Zkopírujte výsledný soubor *. dll* ze složky *bin\Debug* vašeho projektu (například *MessageEditors.dll*) do *%ProgramFiles%\Microsoft Visual Studio\2017 \\ \<edition> \Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Otevřete sadu Visual Studio.

   *Knihovna DLL* je nyní registrována v aplikaci Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Ověření modulů plug-in pomocí testu výkonnosti webu

1. Vytvořte testovací projekt.

2. Vytvořte test výkonnosti webu a v prohlížeči zadejte adresu URL webové služby.

3. Po dokončení nahrávání v Editor testu výkonnosti webu rozbalte požadavek webové služby a vyberte buď **text řetězce** , nebo **binární tělo**.

4. V okně **vlastnosti** vyberte text řetězce nebo binární tělo a zvolte tři tečky **(...)**.

   Zobrazí se dialogové okno **Upravit data těla zprávy HTTP** .

5. Teď můžete data upravit a kliknout na **OK**. Tím se vyvolá platná metoda GetNewValue, která aktualizuje obsah v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> .

## <a name="compile-the-code"></a>Kompilovat kód

Ověřte, zda je cílový rámec pro projekt knihovny ovládacích prvků systému Windows .NET Framework 4,5. Ve výchozím nastavení projekty knihovny ovládacích prvků systému Windows cílí na rozhraní klienta .NET Framework 4,5, které neumožní zahrnutí reference Microsoft. VisualStudio. QualityTools. WebTestFramework.

Další informace naleznete na [stránce aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: Vytvoření modulu plug-in na úrovni požadavků](../test/how-to-create-a-request-level-plug-in.md)
- [Kód vlastní pravidlo extrakce pro test výkonnosti webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kódování vlastního ověřovacího pravidla pro test výkonnosti webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postupy: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programového testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
- [Postupy: vytvoření doplňku sady Visual Studio pro web Performance Výsledky testů Viewer](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
