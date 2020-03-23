---
title: Vytvoření vlastního editoru textu HTTP pro Editor testů výkonu webu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efc9a959fa02b62583e7bf366e8c580b2876a4a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589198"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Postup: Vytvoření vlastního editoru těla HTTP pro Editor testů výkonu webu

Můžete vytvořit vlastní editor obsahu, který umožňuje upravit obsah těla řetězce nebo binární obsah těla žádosti webové služby, například SOAP, REST, asmx, wcf, RIA a další typy požadavků webové služby.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete implementovat tyto druhy editorů:

- **Editor řetězcových obsahů** To je implementováno pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> rozhraní.

- **Binární editor obsahu** To je implementováno pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní.

Tato rozhraní jsou obsažena <xref:Microsoft.VisualStudio.TestTools.WebTesting> v oboru názvů.

## <a name="create-a-windows-control-library-project"></a>Vytvoření projektu knihovny ovládacích prvku systému Windows

1. V sadě Visual Studio vytvořte nový projekt **knihovny Windows Forms Control Library.** Pojmenujte projekt **MessageEditors**.

   Projekt je přidán do nového <xref:System.Windows.Forms.UserControl> řešení a pojmenovaný *UserControl1.cs* je uveden v návrháři.

1. Z **panelu nástrojů**v kategorii Běžné ovládací <xref:System.Windows.Forms.RichTextBox> **prvky** přetáhněte a na povrch UserControl1.

1. V pravém horním![rohu](../test/media/vs_winformsmttagglyph.gif) <xref:System.Windows.Forms.RichTextBox> ovládacího prvku zvolte glyf značky akce (FLyf ) a pak vyberte a **Dock in Parent Container**.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt knihovny formulářů systému Windows a vyberte příkaz **Vlastnosti**.

1. Ve **vlastnostech**vyberte kartu **Aplikace.**

1. V rozevíracím seznamu **Cílová architektura** vyberte rozhraní .NET Framework 4 (nebo novější).

1. Zobrazí se dialogové okno **Změna cílového rámce.**

1. Zvolte **Ano**.

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na uzel **Odkazy** a vyberte **přidat odkaz**.

1. Zobrazí se dialogové okno **Přidat odkaz.**

1. Zvolte . **NET,** posuňte se dolů a vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework** a pak zvolte **OK**.

1. Pokud **Návrhář zobrazení** ještě není otevřený, klikněte v **Průzkumníku řešení**pravým tlačítkem myši na **UserControl1.cs** a vyberte příkaz **Návrhář zobrazení**.

1. Na návrhové ploše klepněte pravým tlačítkem myši a vyberte **zobrazit kód**.

1. (Nepovinné) Změňte název třídy a konstruktoru z UserControl1 na smysluplný název, například MessageEditorControl:

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

1. Přidejte následující vlastnosti, které povolízískání a nastavení textu v poli RichTextBox1. Rozhraní <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> bude používat EditString <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> a bude používat EditByteArray:

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

## <a name="add-a-class-to-the-windows-control-library-project"></a>Přidání třídy do projektu Knihovny ovládacích prvku systému Windows

Přidejte třídu do projektu. Bude použit k implementaci <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> a rozhraní.

**Přehled kódu v tomto postupu**

Editor MessageEditorControl, <xref:System.Windows.Forms.UserControl> který byl vytvořen v předchozím postupu je vytvořen jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Instance messageEditorControl je hostována v dialogovém okně <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> modulu plug-in, který je vytvořen metodou. Navíc messageEditorControl <xref:System.Windows.Forms.RichTextBox> je naplněn obsah v . <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> Vytvoření modulu plug-in však <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> nemůže `true`dojít, pokud vrátí . V případě tohoto editoru <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> vrátí, `true` pokud <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> obsahuje "xml".

Po dokončení úpravy textu řetězce a uživatel klepne **na tlačítko** OK <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> v dialogovém okně modulu plug-in, je volána získat upravený text jako řetězec a aktualizovat **text řetězce** v požadavku v editoru výkonu testu webu.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Vytvoření třídy a implementace rozhraní IStringHttpBodyEditorPlugin

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na projekt knihovny ovládacího prvku formulářů systému Windows a vyberte příkaz **Přidat novou položku**.

   Zobrazí se dialogové okno **Přidat novou položku**.

2. Vyberte **třídu**.

3. Do textového pole **Název** zadejte smysluplný název `MessageEditorPlugins`třídy, například .

4. Zvolte **Přidat**.

   Class1 je přidán do projektu a prezentovány v Editoru kódu.

5. V editoru kódu přidejte následující `using` příkaz:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    ```

6. Vložte do následujícího kódu k implementaci rozhraní:

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

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Přidání modulu IBinaryHttpBodyEditorPlugin do třídy

Implementujte rozhraní <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>.

**Přehled kódu v tomto postupu**

Implementace kódu pro <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní je <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> podobná zahrnuty v předchozím postupu. Binární verze však používá pole bajtů ke zpracování binárních dat namísto řetězce.

Editor Control <xref:System.Windows.Forms.UserControl> vytvořené v prvním postupu je vytvořena jako messageEditorControl:

```csharp
private MessageEditorControl messageEditorControl
```

Instance messageEditorControl je hostována v dialogovém okně <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> modulu plug-in, který je vytvořen metodou. Navíc messageEditorControl <xref:System.Windows.Forms.RichTextBox> je naplněn obsah v . <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> Vytvoření modulu plug-in však <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> nemůže `true`dojít, pokud vrátí . V případě tohoto editoru <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> vrátí, `true` pokud <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> obsahuje "msbin1".

Po dokončení úpravy textu řetězce a uživatel klepne **na tlačítko** OK <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> v dialogovém okně modulu plug-in, je volána získat upravený text jako řetězec a aktualizovat **BinaryHttpBody.Data** v požadavku v Editoru výkonu testu webu.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Přidání modulu IBinaryHttpBodyEditorPlugin do třídy

- Napište nebo zkopírujte následující kód pod třídou XmlMessageEditor přidanou v předchozím postupu k <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> vytvoření instance třídy Msbin1MessageEditor z rozhraní a implementaci požadovaných metod:

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

## <a name="build-and-deploy-the-plug-ins"></a>Vytváření a nasazování modulů plug-in

1. V nabídce **Build** zvolte **Build \<Windows Form Control Library název projektu>**.

2. Zavřete všechny instance sady Visual Studio.

   > [!NOTE]
   > Zavření sady Visual Studio zajistí, že soubor *DLL* není uzamčen před pokusem o jeho zkopírování.

3. Zkopírujte výsledný soubor *DLL* ze složky *bin\ladění* projektu (například *MessageEditors.dll*) do *%ProgramFiles%\Microsoft\\\<Visual Studio\2017 edition>\Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Otevřete sadu Visual Studio.

   *Dll* je nyní registrována v sadě Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Ověření modulů plug-in pomocí testu výkonu webu

1. Vytvořte testovací projekt.

2. Vytvořte test výkonu webu a zadejte adresu URL do prohlížeče webové služby.

3. Po dokončení nahrávání rozbalte v Editoru testů výkonu webu požadavek na webovou službu a vyberte **typ řetězce** nebo **binární tělo**.

4. V okně **Vlastnosti** vyberte buď Tělo řetězce nebo Binární tělo a zvolte tři tečky **(...)**.

   Zobrazí se dialogové okno **Upravit data těla HTTP.**

5. Nyní můžete upravit data a zvolit **OK**. To vyvolá příslušnou metodu GetNewValue pro <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>aktualizaci obsahu v .

## <a name="compile-the-code"></a>Kompilace kódu

Ověřte, zda je cílená architektura pro projekt knihovny ovládacích prvku systému Windows .NET Framework 4.5. Ve výchozím nastavení se projekty knihovny ovládacích oken zaměřují na rozhraní .NET Framework 4.5 Client Framework, což neumožní zahrnutí odkazu Microsoft.VisualStudio.QualityTools.WebTestFramework.

Další informace naleznete v [tématu Stránka aplikace, návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Vytvoření vlastního kódu a modulů plugin pro zátěžové testování](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postup: Vytvoření modulu plug-in na úrovni požadavku](../test/how-to-create-a-request-level-plug-in.md)
- [Kód vlastního pravidla extrakce pro test výkonu webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kód vlastního ověřovacího pravidla pro test výkonu webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postup: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programového testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
- [Postup: Vytvoření doplňku sady Visual Studio pro prohlížeč výsledků testů výkonu webu](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
