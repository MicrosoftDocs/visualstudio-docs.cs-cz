---
title: Sada nástrojů, karta HTML
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90dfae7e891c805a785db8bba00d3c75d2a84bf3
ms.sourcegitcommit: 4708f0ba09b540424efcc344f8438f25432e3d51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384159"
---
# <a name="toolbox-html-tab"></a>Panel nástrojů, Karta HTML

**HTML** součásti, které jsou užitečné pro webové stránky a webové formuláře poskytuje kartu na panelu nástrojů. Chcete-li zobrazit na této kartě, nejprve otevřete dokument pro úpravy v Návrháři HTML. Na **zobrazení** nabídky, klikněte na tlačítko **nástrojů**a potom klikněte na tlačítko **HTML** kartu na panelu nástrojů.

 Chcete-li vytvořit instanci nástroje na **HTML** kartu, buď klikněte dvakrát na nástroj, který ho přidat do aktuálního místa vložení dokumentu nebo vyberte nástroj a přetáhněte ji na požadované pozici na povrchu úpravy.

## <a name="ui-elements"></a>Prvky uživatelského rozhraní

Tyto nástroje jsou k dispozici ve výchozím nastavení na kartě HTML.

**Ukazatel**

![Ukazatel návrháře HTMLpage technologie ASP.NET Mobile](../../ide/reference/media/vxpointer.gif)

Tento nástroj je standardně vybraná, po otevření libovolné kartě panelu nástrojů. Nelze odstranit. Ukazatel umožňuje přetáhněte objekty na návrhové ploše zobrazit, změnit jejich velikost a umístění na stránce nebo formuláře. Další informace najdete v tématu [nástrojů](../../ide/reference/toolbox.md).

**Vstup (tlačítko)**

![Tlačítko HTML webové stránky](../../ide/reference/media/vxbutton.gif)

Vloží `input` prvek `type="button"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Button1"` se tam vloží za první tlačítko `id="Button2"` pro druhý a tak dále.

Při přetažení **vstup (tlačítko)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Vstup (obnovení)**

![Snímek obrazovky HTMLpageResetButton](../../ide/reference/media/vxreset.gif)

Vloží `input` prvek `type="reset"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Reset1"` vložení pro první resetování tlačítko `id="Reset2"` pro druhý a tak dále.

Při přetažení **vstup (obnovení)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Vstup (Odeslat)**

![Snímek obrazovky HTMLpageToolbarSubmitButton](../../ide/reference/media/vxsubmit.gif)

Vloží `input` prvek `type="submit"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Submit1"` se tam vloží za první tlačítko pro odeslání, `id="Submit2"` pro druhý a tak dále.

Při přetažení **vstup (Odeslat)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Vstup (Text)**

![Snímek obrazovky HTMLpageToolbarTextField](../../ide/reference/media/vxtextfield.gif)

Vloží `input` prvek `type="text"` v dokumentu. Chcete-li změnit výchozí text, který se zobrazí, upravte `value` atribut. Ve výchozím nastavení `id="Text1"` je vložen prvního textového pole, `id="Text2"` pro druhý a tak dále.

Při přetažení **vstup (Text)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Doporučujeme, abyste ověřili všechny uživatelský vstup. Další informace najdete v tématu [ověření vstupu uživatele ve webových stránek ASP.NET (Razor) lokality](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Vstup (soubor)**

![Stránka HTML pole souboru](../../ide/reference/media/vxfilefield.gif)

Vloží `input` prvek `type="file"` v dokumentu. Ve výchozím nastavení `id="File1"` se tam vloží za první pole souboru `id="File2"` pro druhý a tak dále.

Při přetažení **vstup (soubor)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Doporučujeme, abyste ověřili všechny uživatelský vstup. Další informace najdete v tématu [ověření vstupu uživatele ve webových stránek ASP.NET (Razor) lokality](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Vstup (heslo)**

![Pole hesla sady Visual Studio](../../ide/reference/media/vxpassword.gif)

Vloží `input` prvek `type="password"`. Ve výchozím nastavení `id="Password1"` se tam vloží za první pole hesla `id="Password2"` pro druhý a tak dále.

Při přetažení **vstup (heslo)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Pokud vaše aplikace odesílá uživatelská jména a hesla, měli byste nakonfigurovat svůj web pomocí vrstvy SSL (Secure Sockets) k šifrování přenosu. Další informace najdete v tématu [zabezpečení připojení](/previous-versions/tn-archive/bb418917(v=technet.10)). Kromě toho se doporučuje, abyste ověřili všechny uživatelský vstup. Další informace najdete v tématu [ověření vstupu uživatele ve webových stránek ASP.NET (Razor) lokality](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Vstup (zaškrtávací políčko)**

![Webová stránka HTML panelu nástrojů možnost zaškrtávací políčko](../../ide/reference/media/vxcheckbox.gif)

Vloží `input` prvek `type="checkbox"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Checkbox1"` se tam vloží za první políčko `id="Checkbox2"` pro druhý a tak dále.

Při přetažení **vstup (zaškrtávací políčko)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Vstup (přepínač)**

![Snímek obrazovky VisualStudioHTMLpageRadioButton](../../ide/reference/media/vxradio.gif)

Vloží `input` prvek `type="radio"`. Pokud chcete změnit text, který se zobrazí, upravte `name` vlastnost. Ve výchozím nastavení `id="Radio1"` se tam vloží za první přepínač `id="Radio2"` pro druhý a tak dále.

Při přetažení **vstup (přepínač)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Vstup (skryté)**

![HTML stránka skryté položky](../../ide/reference/media/vxhidden.gif)

Vloží `input` prvek `type="hidden"`. Ve výchozím nastavení `id="Hidden1"` se tam vloží za první skryté pole `id="Hidden2"` pro druhý a tak dále.

Při přetažení **vstup (skryté)** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Textarea**

![Panel nástrojů HTMLpage textová oblast](../../ide/reference/media/vxtextarea.gif)

Vloží `textarea` elementu. Můžete změnit velikost textového pole, nebo použít jeho posuvníky Chcete-li zobrazit text, který rozšiřuje nad rámec jeho oblast zobrazení. Chcete-li změnit výchozí text, který se zobrazí, upravte `value` atribut. Ve výchozím nastavení `id="textarea1"` je vložen první textová oblast `id=" textarea 2"` pro druhý a tak dále.

Při přetažení **Textarea** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Doporučujeme, abyste ověřili všechny uživatelský vstup. Další informace najdete v tématu [ověření vstupu uživatele ve webových stránek ASP.NET (Razor) lokality](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites).

**Tabulka**

![Snímek obrazovky HTMLpageToolbarTable](../../ide/reference/media/vxtable.gif)

Vloží `table` elementu.

Při přetažení **tabulky** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Obrázek**

![Stránka HTML obrázku položky](../../ide/reference/media/vximage.gif)

Vloží `img` elementu. Upravit tento prvek k určení jeho `src` a jeho `alt` text.

Při přetažení **Image** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<img alt="" src="">
```

**Vyberte**

![HTML stránka sady nástrojů rozevíracího seznamu](../../ide/reference/media/vxdropdown.gif)

Vloží rozevíracího seznamu `select` – element (bez `size` atributu). Ve výchozím nastavení `id="select1"` se tam vloží za první seznam `id="select2"` pro druhý a tak dále.

Při přetažení **vyberte** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Můžete vytvořit více řádky `select` element zvýšením hodnoty vlastnosti size.

**Vodorovná čára**

![Stránka HTML vodorovné položku pravidla](../../ide/reference/media/vxhorizontal.gif)

Vloží `hr` elementu. Chcete-li zvýšit tloušťku čáry, upravte `size` atribut.

Při přetažení **vodorovná čára** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<hr width="100%" size=1>
```

**div**

![Stránka HTML popisek](../../ide/reference/media/vxlabel.gif)

Vloží `div` element, který zahrnuje `ms_positioning="FlowLayout"` atribut. S výjimkou šířku a výšku tato položka je stejný jako do panelu rozložení tok. K formátování textu, který je součástí `div` elementu, přidejte `class="stylename"` atribut otevírací značce.

Při přetažení **Div** na návrhovou plochu zobrazení, je značka jazyka HTML, jako je následující vložen do dokumentu:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Viz také:

- [Panel nástrojů](../../ide/reference/toolbox.md)
