---
title: Panel nástrojů, Karta HTML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31ee75c419870d9047b3892c668c5e4665850654
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292069"
---
# <a name="toolbox-html-tab"></a>Sada nástrojů, karta HTML
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**HTML** součásti, které jsou užitečné pro webové stránky a webové formuláře poskytuje kartu na panelu nástrojů. Chcete-li zobrazit na této kartě, nejprve otevřete dokument pro úpravy v Návrháři HTML. Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**a potom klikněte na tlačítko **HTML** kartu na panelu nástrojů.  
  
 Chcete-li vytvořit instanci nástroje na **HTML** kartu, buď klikněte dvakrát na nástroj, který ho přidat do aktuálního místa vložení dokumentu nebo vyberte nástroj a přetáhněte ji na požadované pozici na povrchu úpravy.  
  
## <a name="tasks"></a>Úlohy  
  
-   [Postupy: Správa oken nástrojů](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
  
-   [Postupy: manipulace s karty panelu nástrojů](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)  
  
## <a name="ui-elements"></a>Prvky uživatelského rozhraní  
 Tyto nástroje jsou k dispozici ve výchozím nastavení na kartě HTML.  
  
 **Ukazatel**  
 ![Technologie ASP.NET Mobile návrháře HTMLpage ukazatel](../../ide/reference/media/vxpointer.gif "vxPointer")  
  
 Tento nástroj je standardně vybraná, po otevření libovolné kartě panelu nástrojů. Nelze odstranit. Ukazatel umožňuje přetáhněte objekty na návrhové ploše zobrazit, změnit jejich velikost a umístění na stránce nebo formuláře. Další informace najdete v tématu [postupy: Správa okna nástrojů](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) a [postupy: manipulace s karty panelu nástrojů](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
 **Vstup (tlačítko)**  
 ![Tlačítko na webové stránce HTML](../../ide/reference/media/vxbutton.gif "vxButton")  
  
 Vloží `input` prvek `type="button"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Button1"` se tam vloží za první tlačítko `id="Button2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (tlačítko)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="Button1" type="button" value="Button" name="Button1">  
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputButton serverového ovládacího prvku](http://msdn.microsoft.com/en-us/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: postupy: vytváření skriptů a upravit obslužné rutiny událostí](http://msdn.microsoft.com/en-us/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [ Mapa obsahu ovládací prvky tlačítka Webový Server](http://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton>, a <xref:System.Web.UI.WebControls.Button>.  
  
 **Vstup (obnovení)**  
 ![Snímek obrazovky HTMLpageResetButton](../../ide/reference/media/vxreset.gif "vxReset")  
  
 Vloží `input` prvek `type="reset"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Reset1"` vložení pro první resetování tlačítko `id="Reset2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (obnovení)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="Reset1" type="reset" value="Reset" name="Reset1">  
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputReset serverového ovládacího prvku](http://msdn.microsoft.com/en-us/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, a <xref:System.Web.UI.WebControls.Button>.  
  
 **Vstup (Odeslat)**  
 ![Snímek obrazovky HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif "vxSubmit")  
  
 Vloží `input` prvek `type="submit"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Submit1"` se tam vloží za první tlačítko pro odeslání, `id="Submit2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (Odeslat)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="Submit1" type="submit" value="Submit" name="Submit1">  
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputSubmit webového serveru ovládacího prvku](http://msdn.microsoft.com/en-us/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, a <xref:System.Web.UI.WebControls.Button>.  
  
 **Vstup (Text)**  
 ![Snímek obrazovky HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif "vxTextfield")  
  
 Vloží `input` prvek `type="text"` v dokumentu. Chcete-li změnit výchozí text, který se zobrazí, upravte `value` atribut. Ve výchozím nastavení `id="Text1"` je vložen prvního textového pole, `id="Text2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (Text)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="Text1" TYPE="text" value="Text Field" name="Text1">  
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputText serverového ovládacího prvku](http://msdn.microsoft.com/en-us/87060d90-a11c-434d-9fc9-b03a8487041e), [Přehled ovládacího prvku textového pole webového serveru](http://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText>, a <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Doporučujeme, abyste ověřili všechny uživatelský vstup. Další informace najdete v tématu [ověřování uživatelského vstupu v ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Vstup (soubor)**  
 ![Stránka HTML pole souboru](../../ide/reference/media/vxfilefield.gif "vxFilefield")  
  
 Vloží `input` prvek `type="file"` v dokumentu. Ve výchozím nastavení `id="File1"` se tam vloží za první pole souboru `id="File2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (soubor)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="File1" type="file" name="File1">  
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputFile serverového ovládacího prvku](http://msdn.microsoft.com/en-us/a817b4a0-056f-4c17-a696-b9fdcde43db6), a <xref:System.Web.UI.HtmlControls.HtmlInputFile>.  
  
> [!IMPORTANT]
>  Doporučujeme, abyste ověřili všechny uživatelský vstup. Další informace najdete v tématu [ověřování uživatelského vstupu v ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Vstup (heslo)**  
 ![Pole hesla Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")  
  
 Vloží `input` prvek `type="password"`. Ve výchozím nastavení `id="Password1"` se tam vloží za první pole hesla `id="Password2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (heslo)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="Password1" type="password" name="Password1">  
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputPassword serverového ovládacího prvku](http://msdn.microsoft.com/en-us/df703dd0-1624-4e5a-a547-c97f2f331b9f), [postupy: nastavení ovládacího prvku webového serveru textové pole pro zadání hesla](http://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310), a [názorný postup: ověřování uživatelských vstupů na webové stránky formuláře](http://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).  
  
> [!IMPORTANT]
>  Pokud aplikace přenáší uživatelská jména a hesla, měli byste nakonfigurovat vašeho webu na používání vrstvy SSL (Secure Sockets) k šifrování přenosu. Další informace najdete v tématu "Zabezpečení připojení pomocí protokolu SSL" [provozní příručce služby IIS](http://go.microsoft.com/fwlink/?linkid=47856). Kromě toho se doporučuje, abyste ověřili všechny uživatelský vstup. Další informace najdete v tématu [ověřování uživatelského vstupu v ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Vstup (zaškrtávací políčko)**  
 ![Webová stránka HTML nástrojů zaškrtávací políčko možnost](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")  
  
 Vloží `input` prvek `type="checkbox"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Checkbox1"` se tam vloží za první políčko `id="Checkbox2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (zaškrtávací políčko)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="Checkbox1" type="checkbox" name="Checkbox1">   
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputCheckBox serverového ovládacího prvku](http://msdn.microsoft.com/en-us/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [zaškrtávací políčko a Přehled ovládacích prvků webového serveru CheckBoxList](http://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox>, a <xref:System.Web.UI.WebControls.CheckBox>.  
  
 **Vstup (přepínač)**  
 ![Snímek obrazovky VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif "vxRadio")  
  
 Vloží `input` prvek `type="radio"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Radio1"` se tam vloží za první přepínač `id="Radio2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (přepínač)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="Radio1" type="radio" name="Radio1">  
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputRadioButton serverového ovládacího prvku](http://msdn.microsoft.com/en-us/6e60ff63-cc57-46ef-bf96-e829e204ba33), [Přehled ovládacích prvků webového serveru RadioButtonListaovládacíhoprvkuRadioButton](http://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton>, a <xref:System.Web.UI.WebControls.RadioButton>.  
  
 **Vstup (skryté)**  
 ![HTML stránka skrytá položka](../../ide/reference/media/vxhidden.gif "vxhidden")  
  
 Vloží `input` prvek `type="hidden"`. Ve výchozím nastavení `id="Hidden1"` se tam vloží za první skryté pole `id="Hidden2"` pro druhý a tak dále.  
  
 Při přetažení **vstup (skryté)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<input id="Hidden1" type="hidden" name="Hidden1">   
```  
  
 Další informace najdete v tématu [vstupní ovládací prvky HTML](http://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe HtmlInputHidden serverového ovládacího prvku](http://msdn.microsoft.com/en-us/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9), a <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.  
  
 **Textarea**  
 ![Oblast textu panelu nástrojů HTMLpage](../../ide/reference/media/vxtextarea.gif "vxTextarea")  
  
 Vloží `textarea` elementu. Můžete změnit velikost textového pole, nebo použít jeho posuvníky Chcete-li zobrazit text, který rozšiřuje nad rámec jeho oblast zobrazení. Chcete-li změnit výchozí text, který se zobrazí, upravte `value` atribut. Ve výchozím nastavení `id="textarea1"` je vložen první textová oblast `id=" textarea 2"` pro druhý a tak dále.  
  
 Při přetažení **Textarea** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>   
```  
  
 Další informace najdete v tématu [deklarativní syntaxe HtmlTextArea serverového ovládacího prvku](http://msdn.microsoft.com/en-us/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea>, a <xref:System.Web.UI.WebControls.TextBox>.  
  
> [!IMPORTANT]
>  Doporučujeme, abyste ověřili všechny uživatelský vstup. Další informace najdete v tématu [ověřování uživatelského vstupu v ASP.NET Web Pages](http://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).  
  
 **Tabulka**  
 ![Snímek obrazovky HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable")  
  
 Vloží `table` elementu.  
  
 Při přetažení **tabulky** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>   
```  
  
 Další informace najdete v tématu [deklarativní syntaxe HtmlTable serverového ovládacího prvku](http://msdn.microsoft.com/en-us/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [tabulka řádků tabulky a Přehled ovládacího prvku webového serveru buňky tabulky](http://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable>, a <xref:System.Web.UI.WebControls.Table>.  
  
 **Obrázek**  
 ![Stránka HTML obrázku položky](../../ide/reference/media/vximage.gif "vxImage")  
  
 Vloží `img` elementu. Upravit tento prvek k určení jeho `src` a jeho `alt` text.  
  
 Při přetažení **Image** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<img alt="" src="">  
```  
  
 Další informace najdete v tématu [deklarativní syntaxe HtmlImage serverového ovládacího prvku](http://msdn.microsoft.com/en-us/528430e8-ced1-47d1-8db2-942e734a61f6), [Přehled ovládacího prvku webového serveru Image](http://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage>, a <xref:System.Web.UI.WebControls.Image>.  
  
 **Vyberte**  
 ![Stránka HTML rozevírací seznam nástrojů](../../ide/reference/media/vxdropdown.gif "vxDropdown")  
  
 Vloží rozevíracího seznamu `select` – element (bez `size` atributu). Ve výchozím nastavení `id="select1"` se tam vloží za první seznam `id="select2"` pro druhý a tak dále.  
  
 Při přetažení **vyberte** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<select id="select1" name="select1"><option selected></option></select>  
```  
  
 Můžete vytvořit více řádky `select` element zvýšením hodnoty vlastnosti size.  
  
 Další informace najdete v tématu [deklarativní syntaxe serverového ovládacího prvku HtmlSelect](http://msdn.microsoft.com/en-us/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: postupy: vytváření skriptů a upravit obslužné rutiny událostí](http://msdn.microsoft.com/en-us/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Přehled ovládacího prvku webového serveru DropDownList](http://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), [Přehled ovládacího prvku ListBox webového serveru](http://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97), <xref:System.Web.UI.HtmlControls.HtmlSelect>, a <xref:System.Web.UI.WebControls.DropDownList>.  
  
 **Vodorovná čára**  
 ![Stránka HTML vodorovné položku pravidla](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")  
  
 Vloží `hr` elementu. Chcete-li zvýšit tloušťku čáry, upravte `size` atribut.  
  
 Při přetažení **vodorovná čára** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<hr width="100%" size=1>   
```  
  
 Další informace najdete v tématu [ovládací prvek vodorovné pravidlo](http://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).  
  
 **div**  
 ![Stránka HTML popisek](../../ide/reference/media/vxlabel.gif "vxLabel")  
  
 Vloží `div` element, který zahrnuje `ms_positioning="FlowLayout"` atribut. S výjimkou šířku a výšku tato položka je stejný jako do panelu rozložení tok. K formátování textu, který je součástí `div` elementu, přidejte `class="stylename"` atribut otevírací značce.  
  
 Při přetažení **Div** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:  
  
```  
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>  
```  
  
 Další informace najdete v tématu [ovládací prvek Div](http://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Přehled ovládacího prvku webového serveru popisek](http://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac), a <xref:System.Web.UI.WebControls.Label>.  
  
## <a name="see-also"></a>Viz také  
 [Panel nástrojů](../../ide/reference/toolbox.md)   
 [Standardní kartě panelu nástrojů](http://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)   
 [Ovládací prvky HTML](http://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be)



