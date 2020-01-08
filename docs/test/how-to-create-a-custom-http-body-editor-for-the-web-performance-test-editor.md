---
title: Vytvoření vlastního editoru těla protokolu HTTP pro Editor testu výkonnosti webu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, custom HTTP body editor
ms.assetid: a0b2d8ff-3e2a-487e-9172-90047174f336
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efc9a959fa02b62583e7bf366e8c580b2876a4a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589198"
---
# <a name="how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor"></a>Postupy: vytvoření vlastního protokolu HTTP text editoru pro Editor testu výkonnosti webu

Můžete vytvořit vlastní editor obsahu, který umožňuje upravovat obsah řetězce textu nebo binární tělo obsah požadavku webové služby, například SOAP, REST, asmx, wcf, RIA a jiných typů požadavek webové služby.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Můžete implementovat tyto druhy editory:

- **Řetězcový editor obsahu** Toto je implementováno pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> rozhraní.

- **Binární editor obsahu** Toto je implementováno pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní.

Tato rozhraní jsou obsažena v <xref:Microsoft.VisualStudio.TestTools.WebTesting> oboru názvů.

## <a name="create-a-windows-control-library-project"></a>Vytvoření projektu knihovny ovládacích prvků Windows

1. V aplikaci Visual Studio vytvořte nový projekt **knihovny ovládacích prvků model Windows Forms** . Pojmenujte projekt **MessageEditors**.

   Projekt je přidán do nového řešení a <xref:System.Windows.Forms.UserControl> s názvem *UserControl1.cs* je předložen v návrháři.

1. Z **nástrojů**v části **běžné ovládací prvky** kategorie, přetáhněte <xref:System.Windows.Forms.RichTextBox> na povrch UserControl1.

1. Zvolte piktogram akce (![piktogram inteligentní](../test/media/vs_winformsmttagglyph.gif)) v pravém horním rohu <xref:System.Windows.Forms.RichTextBox> ovládací prvek a potom vyberte a **ukotvit v nadřazeném kontejneru**.

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt Windows Forms Library a vyberte **vlastnosti**.

1. V **vlastnosti**, vyberte **aplikace** kartu.

1. V rozevíracím seznamu **cílové rozhraní** vyberte .NET Framework 4 (nebo novější).

1. **Změnit cílový rámec** se zobrazí dialogové okno.

1. Zvolte **Ano**.

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel a vyberte možnost **přidat odkaz**.

1. **Přidat odkaz** se zobrazí dialogové okno.

1. Vyberte. **NET** kartu, posuňte se dolů a vyberte **Microsoft.VisualStudio.QualityTools.WebTestFramework** a klikněte na tlačítko **OK**.

1. Pokud **Návrhář zobrazení** není stále otevřen v **Průzkumníka řešení**, klikněte pravým tlačítkem na **UserControl1.cs** a pak vyberte **Návrhář zobrazení**.

1. Na návrhové ploše, klikněte pravým tlačítkem a vyberte **zobrazit kód**.

1. (Volitelné) Změňte název třídy a konstruktoru z UserControl1 na smysluplný název, například MessageEditorControl:

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

1. Přidejte následující vlastnosti umožňující získání a nastavení textu v RichTextBox1. <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> Rozhraní bude používat EditString a <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> bude používat EditByteArray:

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

## <a name="add-a-class-to-the-windows-control-library-project"></a>Přidání třídy do projektu knihovny ovládací prvků Windows

Přidání třídy do projektu. Se použije k implementaci <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> a <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní.

**Přehled kódu v tomto postupu**

MessageEditorControl <xref:System.Windows.Forms.UserControl> , který byl vytvořen v předchozím postupu je vytvořena instance messageeditorcontrol:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl instance je hostována v dialogovém okně modulu plug-in, který je vytvořen pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.CreateEditor*> metody. Kromě toho pole messageEditorControl <xref:System.Windows.Forms.RichTextBox> je vyplněno obsahem v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Vytvoření modulu plug-in nelze však dojít, pokud není <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> vrátí `true`. V případě tohoto editoru <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.SupportsContentType*> vrátí `true` Pokud <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> obsahuje "xml".

Po dokončení úprav textu řetězce a při kliknutí **OK** v dialogovém okně modulu plug-in <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin.GetNewValue*> je volána k získání upraveného textu jako řetězce a aktualizaci **tělo řetězce** v požadavku na webu Editoru testování výkonu.

### <a name="create-a-class-and-implement-the-istringhttpbodyeditorplugin-interface"></a>Vytvoření třídy a implementace rozhraní IStringHttpBodyEditorPlugin

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt Knihovna ovládacích prvků formulářů Windows a vyberte **přidat novou položku**.

   **Přidat novou položku** se zobrazí dialogové okno.

2. Vyberte **třídy**.

3. V **název** textové pole, zadejte smysluplný název pro třídu, například `MessageEditorPlugins`.

4. Zvolte **přidat**.

   Class1 je přidána do projektu a zobrazí v editoru kódu.

5. V editoru kódu přidejte následující příkaz `using`:

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

## <a name="add-a-ibinaryhttpbodyeditorplugin-to-the-class"></a>Přidání modulu Plugin IBinaryHttpBodyEditorPlugin do třídy

Implementace <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní.

**Přehled kódu v tomto postupu**

Implementace kódu pro <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní je podobný <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin> popsané v předchozím postupu. Binární verze však používá pole bajtů ke zpracování binárních dat namísto řetězce.

MessageEditorControl <xref:System.Windows.Forms.UserControl> vytvořili v prvním postupu je vytvořena instance messageeditorcontrol:

```csharp
private MessageEditorControl messageEditorControl
```

MessageEditorControl instance je hostována v dialogovém okně modulu plug-in, který je vytvořen pomocí <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.CreateEditor*> metody. Kromě toho pole messageEditorControl <xref:System.Windows.Forms.RichTextBox> je vyplněno obsahem v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>. Vytvoření modulu plug-in nelze však dojít, pokud není <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> vrátí `true`. V případě tohoto editoru <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.SupportsContentType*> vrátí `true` Pokud <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody.ContentType*> v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody> obsahuje "msbin1".

Po dokončení úprav textu řetězce a při kliknutí **OK** v dialogovém okně modulu plug-in <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin.GetNewValue*> je volána k získání upraveného textu jako řetězce a aktualizaci **BinaryHttpBody.Data** v požadavku v editoru testování výkonu webu.

### <a name="to-add-the-ibinaryhttpbodyeditorplugin-to-the-class"></a>Přidání modulu Plugin IBinaryHttpBodyEditorPlugin do třídy

- Napište nebo zkopírujte následující kód ve třídě XmlMessageEditor přidaný v předchozím postupu k vytvoření instance třídy Msbin1MessageEditor z <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin> rozhraní a implementuje požadované metody:

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

## <a name="build-and-deploy-the-plug-ins"></a>Vytvoření a nasazení modulů plug-in

1. Na **sestavení** nabídce zvolte **sestavení \<název projektu ovládacího prvku knihovny formulář Windows >** .

2. Zavřete všechny instance sady Visual Studio.

   > [!NOTE]
   > Zavření sady Visual Studio zajišťuje, že *.dll* souboru není uzamčen před pokusem o zkopírování.

3. Zkopírujte výsledný soubor *. dll* ze složky *bin\Debug* vašeho projektu (například *MessageEditors. dll*) do *%ProgramFiles%\Microsoft Visual Studio\2017\\\<Edition > \Common7\IDE\PrivateAssemblies\WebTestPlugins*.

4. Otevřít Visual Studio.

   *.Dll* je teď zaregistrované pomocí sady Visual Studio.

## <a name="verify-the-plug-ins-using-a-web-performance-test"></a>Zkontrolujte moduly plug-in pomocí testu výkonnosti webu

1. Vytvoření testovacího projektu.

2. Vytvoření testu výkonnosti webu a zadejte adresu URL v prohlížeči na webovou službu.

3. Po dokončení nahrávání v editoru testu výkonnosti webu, rozbalte požadavek webové služby a vyberte buď **tělo řetězce** nebo **binární tělo**.

4. V okně **vlastnosti** vyberte text řetězce nebo binární tělo a zvolte tři tečky **(...)** .

   **Upravit Data těla protokolu HTTP** se zobrazí dialogové okno.

5. Teď můžete data upravit a zvolit **OK**. To vyvolá vhodnou metodu GetNewValue k aktualizaci obsahu v <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>.

## <a name="compile-the-code"></a>Kompilace kódu

Ověřte, zda cílové rozhraní framework pro projekt Knihovna ovládacích prvků Windows je .NET Framework 4.5. Projekty knihovny ovládacích prvků Windows standardně cílit na rozhraní .NET Framework 4.5 Client, který nedovolí zařazení odkazu na Microsoft.VisualStudio.QualityTools.WebTestFramework.

Další informace najdete v tématu [stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IStringHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IBinaryHttpBodyEditorPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.IHttpBody>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.RichTextBox>
- [Vytvoření vlastního kódu a modulů Plugin pro zátěžové testy](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Postupy: vytvoření modulu Plugin úrovni požadavků](../test/how-to-create-a-request-level-plug-in.md)
- [Kód vlastního pravidla extrakce pro test výkonnosti webu](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kód vlastního ověřovacího pravidla pro test výkonnosti webu](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Postupy: vytvoření modulu Plugin pro zátěžový test](../test/how-to-create-a-load-test-plug-in.md)
- [Generování a spuštění programový test výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
- [Postupy: Vytvoření doplňku sady Visual Studio pro prohlížeč výsledků testu výkonnosti webu](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)
