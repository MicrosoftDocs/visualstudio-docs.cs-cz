---
title: Panel nástrojů, karta HTML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
ms.assetid: 9bfdd3b8-f5ac-4a5f-bdbf-c2b4e97641d8
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b7ca3179d3e4883f8a2867e13cbdd5e874d60462
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297775"
---
# <a name="toolbox-html-tab"></a>Sada nástrojů, karta HTML
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Karta **HTML** v sadě nástrojů poskytuje komponenty, které jsou užitečné pro webové stránky a webové formuláře. Chcete-li zobrazit tuto kartu, nejprve otevřete dokument pro úpravy v Návrháři HTML. V nabídce **zobrazení** klikněte na **panel nástrojů**a pak klikněte na kartu **HTML** sady nástrojů.

 Chcete-li vytvořit instanci nástroje na kartě **HTML** , buď poklikejte na nástroj a přidejte ho do dokumentu v aktuálním místě vložení, nebo ho vyberte a přetáhněte ho na požadovanou pozici na ploše pro úpravy.

## <a name="tasks"></a>Úkoly

- [Postupy: Správa okna nástrojů](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)

- [Postupy: manipulace s kartami nástrojů](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)

## <a name="ui-elements"></a>Prvky uživatelského rozhraní
 Ve výchozím nastavení jsou na kartě HTML k dispozici následující nástroje.

 **Ukazatel** ![ASP.NET Mobile Designer HTMLpage](../../ide/reference/media/vxpointer.gif "vxPointer")

 Tento nástroj je vybraný ve výchozím nastavení, když se otevře kterákoli karta panelu nástrojů. Nedá se odstranit. Ukazatel umožňuje přetahovat objekty na zobrazení Návrh plochu, měnit jejich velikost a přemístit je na stránce nebo formuláři. Další informace naleznete v tématu [How to: manage a Window panel nástrojů](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) a [How to: manipulace s kartami nástrojů](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Tlačítko pro vložení ![webové stránky ve formátu HTML](../../ide/reference/media/vxbutton.gif "vxButton") **(tlačítko)**

 Vloží `input` prvek `type="button"`. Chcete-li změnit zobrazený text, upravte vlastnost `name`. Ve výchozím nastavení je `id="Button1"` vložen pro první tlačítko, `id="Button2"` pro druhý a tak dále.

 Při přetažení **vstupu (Button)** na zobrazení Návrh plochu se do dokumentu vloží kód HTML jako následující:

```
<input id="Button1" type="button" value="Button" name="Button1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe ovládacího prvku serveru HtmlInputButton](https://msdn.microsoft.com/99ccf7fb-7e2a-4ba1-bcd9-981b619a16aa), [NIB: postupy: vytváření skriptů a úprav obslužných rutin událostí](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [webový server tlačítek ovládací prvky obsahu](https://msdn.microsoft.com/library/66b3ce28-3b93-4f0a-951f-42fb5bb5fddf), <xref:System.Web.UI.HtmlControls.HtmlInputButton>, <xref:System.Web.UI.HtmlControls.HtmlButton>a <xref:System.Web.UI.WebControls.Button>.

 **Vstup (reset)** ![HTMLpageResetButton snímek obrazovky](../../ide/reference/media/vxreset.gif "vxReset")

 Vloží `input` prvek `type="reset"`. Chcete-li změnit zobrazený text, upravte vlastnost `name`. Ve výchozím nastavení je `id="Reset1"` vložen pro tlačítko první Reset, `id="Reset2"` pro druhý atd.

 Při přetažení **vstupu (reset)** na zobrazení Návrh plochu se do dokumentu vloží kód HTML podobný následujícímu:

```
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe ovládacího prvku serveru HtmlInputReset](https://msdn.microsoft.com/cfc1f1fb-d33a-464d-9bb5-204e66174979), <xref:System.Web.UI.HtmlControls.HtmlInputButton>a <xref:System.Web.UI.WebControls.Button>.

 **Vstup (Odeslat)** ![HTMLpageToolbarSubmitButton snímek obrazovky](../../ide/reference/media/vxsubmit.gif "vxSubmit")

 Vloží `input` prvek `type="submit"`. Chcete-li změnit zobrazený text, upravte vlastnost `name`. Ve výchozím nastavení je `id="Submit1"` vložen pro první tlačítko Odeslat, `id="Submit2"` pro druhý atd.

 Při přetažení **vstupu (Odeslat)** na zobrazení Návrh plochu se do dokumentu vloží kód HTML podobný následujícímu:

```
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe ovládacího prvku serveru HtmlInputSubmit](https://msdn.microsoft.com/eef2a157-f184-4ce9-b256-d1eacc7930f2), <xref:System.Web.UI.HtmlControls.HtmlInputButton>a <xref:System.Web.UI.WebControls.Button>.

 **Vstup (text)** ![HTMLpageToolbarTextField snímek obrazovky](../../ide/reference/media/vxtextfield.gif "vxTextfield")

 Vloží `input` prvek `type="text"` v dokumentu. Chcete-li změnit výchozí zobrazený text, upravte atribut `value`. Ve výchozím nastavení se `id="Text1"` vloží do prvního textového pole, `id="Text2"` pro druhý a tak dále.

 Když přetáhnete **vstup (text)** na zobrazení Návrh plochu, do dokumentu se vloží kód HTML podobný následujícímu:

```
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe ovládacího prvku HtmlInputText serveru](https://msdn.microsoft.com/87060d90-a11c-434d-9fc9-b03a8487041e), [Přehled ovládacího prvku webového serveru TextBox](https://msdn.microsoft.com/library/ab354bc1-f23a-48fc-93d8-d4d7c1b7396f), <xref:System.Web.UI.HtmlControls.HtmlInputText>a <xref:System.Web.UI.WebControls.TextBox>.

> [!IMPORTANT]
> Doporučuje se ověřovat všechny vstupy uživatelů. Další informace najdete v tématu [ověření vstupu uživatele na webových stránkách ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Vstupní (soubor)** ![pole souboru HTML stránky](../../ide/reference/media/vxfilefield.gif "vxFilefield")

 Vloží `input` prvek `type="file"` v dokumentu. Ve výchozím nastavení se `id="File1"` vloží do pole první soubor, `id="File2"` pro druhý atd.

 Když přetáhnete **vstup (soubor)** na zobrazení Návrh plochu, do dokumentu se vloží kód HTML podobný následujícímu:

```
<input id="File1" type="file" name="File1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxi ovládacího prvku serveru HtmlInputFile](https://msdn.microsoft.com/a817b4a0-056f-4c17-a696-b9fdcde43db6)a <xref:System.Web.UI.HtmlControls.HtmlInputFile>.

> [!IMPORTANT]
> Doporučuje se ověřovat všechny vstupy uživatelů. Další informace najdete v tématu [ověření vstupu uživatele na webových stránkách ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Input (Password)** – ![pole hesla sady Visual Studio](../../ide/reference/media/vxpassword.gif "vxPassword")

 Vloží `input` prvek `type="password"`. Ve výchozím nastavení se `id="Password1"` vloží do pole první heslo, `id="Password2"` pro druhý atd.

 Při přetažení **vstupu (hesla)** na zobrazení Návrh plochu se do dokumentu vloží kód HTML jako následující:

```
<input id="Password1" type="password" name="Password1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxe ovládacího prvku HtmlInputPassword serveru](https://msdn.microsoft.com/df703dd0-1624-4e5a-a547-c97f2f331b9f), [Postupy: nastavení ovládacího prvku webového serveru TextBox pro zadání hesla](https://msdn.microsoft.com/library/5b5069f3-64a1-435a-aee6-da263f4e6310)a [Návod: ověřování vstupu uživatele na stránce webových formulářů](https://msdn.microsoft.com/library/7141d6ba-34f3-410b-b5cd-2102a24cb436).

> [!IMPORTANT]
> Pokud vaše aplikace přenáší uživatelská jména a hesla, měli byste web nakonfigurovat tak, aby používal SSL (Secure Sockets Layer) (SSL) k šifrování přenosu. Další informace najdete v části zabezpečení připojení pomocí SSL v [provozní příručce služby IIS](https://go.microsoft.com/fwlink/?linkid=47856). Kromě toho se doporučuje ověřit všechny vstupy uživatelů. Další informace najdete v tématu [ověření vstupu uživatele na webových stránkách ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 **Input (zaškrtávací políčko)** ![možnost panelu nástrojů HTML webové stránky](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")

 Vloží `input` prvek `type="checkbox"`. Chcete-li změnit zobrazený text, upravte vlastnost `name`. Ve výchozím nastavení je `id="Checkbox1"` vložen pro první zaškrtávací políčko, `id="Checkbox2"` pro druhý atd.

 Při přetažení **vstupu (zaškrtávací políčko)** na zobrazení Návrh plochu se do dokumentu vloží kód HTML jako následující:

```
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), ovládací prvky webového serveru [HtmlInputCheckBox deklarativní syntaxe](https://msdn.microsoft.com/4a509586-89d8-4ccf-a0b8-b9160ce6e4a6), [zaškrtávací políčko a webový server CheckBoxList – přehled](https://msdn.microsoft.com/library/3028dfd3-e2c5-451d-9150-d02c8ffb92bf), <xref:System.Web.UI.HtmlControls.HtmlInputCheckBox>a <xref:System.Web.UI.WebControls.CheckBox>.

 **Vstup (Radio)** ![VisualStudioHTMLpageRadioButton snímek obrazovky](../../ide/reference/media/vxradio.gif "vxRadio")

 Vloží `input` prvek `type="radio"`. Chcete-li změnit zobrazený text, upravte vlastnost `name`. Ve výchozím nastavení je `id="Radio1"` vložen pro první přepínač, `id="Radio2"` za sekundu a tak dále.

 Při přetažení **vstupu (Radio)** na zobrazení Návrh plochu se do dokumentu vloží kód HTML podobný následujícímu:

```
<input id="Radio1" type="radio" name="Radio1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), deklarativní syntaxe ovládacích prvků webového serveru [HtmlInputRadioButton Server](https://msdn.microsoft.com/6e60ff63-cc57-46ef-bf96-e829e204ba33), [RadioButton a RadioButtonList. Přehled](https://msdn.microsoft.com/library/20eb383c-4b59-432b-bba3-e9d785107747), <xref:System.Web.UI.HtmlControls.HtmlInputRadioButton>a <xref:System.Web.UI.WebControls.RadioButton>.

 **Vstupní (skrytá)** ![Skrytá položka stránky HTML](../../ide/reference/media/vxhidden.gif "vxhidden")

 Vloží `input` prvek `type="hidden"`. Ve výchozím nastavení se `id="Hidden1"` vloží do prvního skrytého pole, `id="Hidden2"` pro druhý atd.

 Když přetáhnete **vstup (skrytý)** na zobrazení Návrh plochu, do dokumentu se vloží kód HTML podobný následujícímu:

```
<input id="Hidden1" type="hidden" name="Hidden1">
```

 Další informace naleznete v tématu [ovládací prvky vstupu HTML](https://msdn.microsoft.com/library/2ba82c6b-dff7-4b73-b1c2-9e76a48a69de), [deklarativní syntaxi ovládacího prvku serveru HtmlInputHidden](https://msdn.microsoft.com/4194e44d-1d74-4bfc-9cc7-743a2e1ea5f9)a <xref:System.Web.UI.HtmlControls.HtmlInputHidden>.

 ![Oblast textu panelu nástrojů HTMLpage](../../ide/reference/media/vxtextarea.gif "vxTextarea") ovládacího prvku textarea

 Vloží prvek `textarea`. Můžete změnit velikost textové oblasti nebo použít posuvníky k zobrazení textu, který je delší než oblast zobrazení. Chcete-li změnit výchozí zobrazený text, upravte atribut `value`. Ve výchozím nastavení je `id="textarea1"` vložena první textová oblast, `id=" textarea 2"` pro druhý atd.

 Při přetažení **komponenty TextArea** na zobrazení Návrh plochu se do dokumentu vloží kód HTML jako následující:

```
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

 Další informace naleznete v tématu [deklarativní syntaxe ovládacího prvku serveru HtmlTextArea](https://msdn.microsoft.com/5a103ffa-235b-4452-ba2b-a4fb8ba8cb87), <xref:System.Web.UI.HtmlControls.HtmlTextArea>a <xref:System.Web.UI.WebControls.TextBox>.

> [!IMPORTANT]
> Doporučuje se ověřovat všechny vstupy uživatelů. Další informace najdete v tématu [ověření vstupu uživatele na webových stránkách ASP.NET](https://msdn.microsoft.com/library/4ad3dacb-89e0-4cee-89ac-40a3f2a85461).

 ![Snímek HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif "vxTable") s **tabulkou**

 Vloží prvek `table`.

 Když přetáhnete **tabulku** na zobrazení Návrh plochu, do dokumentu se vloží kód HTML podobný následujícímu:

```
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

 Další informace naleznete v tématu [deklarativní syntaxe serverového ovládacího prvku HTML](https://msdn.microsoft.com/625b06d8-0f69-4112-a1d4-8ef2a9fbcda9), [tabulka, TableRow a Přehled ovládacího prvku webového serveru TableCell](https://msdn.microsoft.com/library/2fbd0582-cf69-4c8d-9e35-21f35e2cee1a), <xref:System.Web.UI.HtmlControls.HtmlTable>a <xref:System.Web.UI.WebControls.Table>.

 ![Položka obrázku stránky HTML](../../ide/reference/media/vximage.gif "vxImage") obrázku

 Vloží prvek `img`. Upravte tento prvek a určete jeho `src` a jeho `alt` text.

 Při přetažení **obrázku** na zobrazení Návrh plochu se do dokumentu vloží kód HTML podobný následujícímu:

```
<img alt="" src="">
```

 Další informace naleznete v tématu [deklarativní syntaxe ovládacího prvku Server HtmlImage](https://msdn.microsoft.com/528430e8-ced1-47d1-8db2-942e734a61f6), [Přehled webového serveru s obrázkem](https://msdn.microsoft.com/library/096a8d8d-58ee-4ee8-ab82-6594a0f3a0a9), <xref:System.Web.UI.HtmlControls.HtmlImage>, <xref:System.Web.UI.HtmlControls.HtmlInputImage>a <xref:System.Web.UI.WebControls.Image>.

 Rozevírací nabídka pro **Výběr** ![stránky HTML](../../ide/reference/media/vxdropdown.gif "vxDropdown")

 Vloží `select` prvek rozevíracího seznamu (bez atributu `size`). Ve výchozím nastavení je `id="select1"` vložen pro první seznam, `id="select2"` pro druhý a tak dále.

 Když přetáhnete **možnost vybrat** na zobrazení Návrh plochu, do dokumentu se vloží kód HTML podobný následujícímu:

```
<select id="select1" name="select1"><option selected></option></select>
```

 Můžete vytvořit víceřádkový `select` element zvětšením hodnoty vlastnosti Size.

 Další informace naleznete v tématu [deklarativní syntaxe ovládacího prvku serveru HtmlSelect](https://msdn.microsoft.com/ee93bdec-b343-441a-a8ff-56ffcafe9ae5), [NIB: postupy: vytváření skriptů a úprav obslužných rutin událostí](https://msdn.microsoft.com/69d71d13-c68b-4ecd-869b-a42edf6d1f6d), [Přehled ovládacího prvku webového serveru DropDownList](https://msdn.microsoft.com/library/517dd1a4-8df3-4c9f-8c89-1549a1aee608), přehled [ovládacího prvku webového serveru, přehled](https://msdn.microsoft.com/library/c08ee025-787a-408d-858e-a4a5fdb61d97)<xref:System.Web.UI.HtmlControls.HtmlSelect>a <xref:System.Web.UI.WebControls.DropDownList>.

 ![Položka vodorovného pravidla stránky HTML](../../ide/reference/media/vxhorizontal.gif "vxHorizontal") **vodorovného pravidla**

 Vloží prvek `hr`. Chcete-li zvětšit tloušťku čáry, upravte atribut `size`.

 Když na zobrazení Návrh plochu přetáhnete **horizontální pravidlo** , do dokumentu se vloží kód HTML podobný následujícímu:

```
<hr width="100%" size=1>
```

 Další informace najdete v tématu [ovládací prvek vodorovných pravidel HTML](https://msdn.microsoft.com/library/bf6df0a8-9844-404d-8a9a-3455b0180f2f).

 **Div** – ![popisek stránky HTML](../../ide/reference/media/vxlabel.gif "vxLabel")

 Vloží `div` element, který obsahuje atribut `ms_positioning="FlowLayout"`. S výjimkou šířky a výšky je tato položka shodná s panelem rozložení toku. Chcete-li formátovat text obsažený v prvku `div`, přidejte do počáteční značky atribut `class="stylename"`.

 Když přetáhnete **div** na zobrazení Návrh plochu, do dokumentu se vloží kód HTML jako následující:

```
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

 Další informace naleznete v tématu [ovládací prvky DIV HTML](https://msdn.microsoft.com/library/585fa702-4408-4af1-a92b-68d77ee5e995), [Přehled ovládacího prvku webového serveru Label](https://msdn.microsoft.com/library/990558d1-4b22-4f28-b100-78a434b3c5ac)a <xref:System.Web.UI.WebControls.Label>.

## <a name="see-also"></a>Viz také
 Karta standard [panelu nástrojů](../../ide/reference/toolbox.md) , [ovládací prvky HTML](https://msdn.microsoft.com/library/83bc6f7e-a2b5-4fe9-9a34-eb34aef673be) [sady nástrojů](https://msdn.microsoft.com/library/35e9320d-fcbd-474b-8b8f-55705e9a1870)
