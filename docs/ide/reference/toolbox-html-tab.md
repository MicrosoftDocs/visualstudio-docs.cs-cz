---
title: Sada nástrojů, karta HTML
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0489f534466149a437384d4f21e34f1fa9e98c5b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596434"
---
# <a name="toolbox-html-tab"></a>Panel nástrojů, karta HTML

Karta **HTML** v panelu nástrojů obsahuje komponenty, které jsou užitečné na webových stránkách a webových formulářích. Chcete-li tuto kartu zobrazit, otevřete nejprve dokument pro úpravy v návrháři HTML. V nabídce **View** klikněte na **Panel nástrojů**a potom klikněte na kartu **HTML** v panelu nástrojů.

Chcete-li vytvořit instanci nástroje na kartě **HTML,** poklepejte na nástroj a přidejte jej do dokumentu v aktuálním kurzoru nebo nástroj vyberte a přetáhněte ho do požadované polohy na editační ploše.

## <a name="ui-elements"></a>Prvky uživatelského rozhraní

Následující nástroje jsou ve výchozím nastavení k dispozici na kartě HTML.

**Ukazatel**

![ukazatel HTMLpage návrháře ASP.NET mobilního](../../ide/reference/media/vxpointer.gif)

Tento nástroj je vybrán ve výchozím nastavení, když se otevře libovolná karta Panel u nástrojů. Nelze jej odstranit. Ukazatel umožňuje přetáhnout objekty na povrch návrhového pohledu, změnit jejich velikost a změnit jejich umístění na stránce nebo formuláři. Další informace naleznete v [tématu Toolbox](../../ide/reference/toolbox.md).

**Vstup (tlačítko)**

![Tlačítko webové stránky HTML](../../ide/reference/media/vxbutton.gif)

Vloží `input` prvek . `type="button"` Chcete-li změnit zobrazený text, `name` upravte vlastnost. Ve výchozím `id="Button1"` nastavení je vložen pro `id="Button2"` první tlačítko, pro druhé a tak dále.

Když přetáhnete **vstup (tlačítko)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**Vstup (Reset)**

![HTMLpageResetButton snímek obrazovky](../../ide/reference/media/vxreset.gif)

Vloží `input` prvek . `type="reset"` Chcete-li změnit zobrazený text, `name` upravte vlastnost. Ve výchozím `id="Reset1"` nastavení je vložen pro `id="Reset2"` první tlačítko reset, pro druhé a tak dále.

Když přetáhnete **vstup (Obnovit)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**Vstup (Odeslat)**

![HTMLpageToolbarSubmitButton snímek obrazovky](../../ide/reference/media/vxsubmit.gif)

Vloží `input` prvek . `type="submit"` Chcete-li změnit zobrazený text, `name` upravte vlastnost. Ve výchozím `id="Submit1"` nastavení je vložen pro `id="Submit2"` první tlačítko odeslat, pro druhý a tak dále.

Když přetáhnete **input (odeslat)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**Vstup (text)**

![HTMLpageToolbarTextField – snímek obrazovky](../../ide/reference/media/vxtextfield.gif)

Vloží prvek `input` `type="text"` do dokumentu. Chcete-li změnit výchozí zobrazený text, upravte `value` atribut. Ve výchozím `id="Text1"` nastavení je vložen pro `id="Text2"` první textové pole, pro druhé a tak dále.

Když přetáhnete **vstup (text)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>Doporučujeme ověřit všechny vstupy uživatele. Další informace naleznete [v tématu Ověřování vstupu uživatele v ASP.NET webech webových stránek (Razor).](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Vstup (soubor)**

![Pole souboru stránky HTML](../../ide/reference/media/vxfilefield.gif)

Vloží prvek `input` `type="file"` do dokumentu. Ve výchozím `id="File1"` nastavení je vložen pro `id="File2"` první pole souboru, pro druhý a tak dále.

Když přetáhnete **input (file)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> Doporučujeme ověřit všechny vstupy uživatele. Další informace naleznete [v tématu Ověřování vstupu uživatele v ASP.NET webech webových stránek (Razor).](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Vstup (heslo)**

![Pole s heslem sady Visual Studio](../../ide/reference/media/vxpassword.gif)

Vloží `input` prvek . `type="password"` Ve výchozím `id="Password1"` nastavení je vložen pro `id="Password2"` první heslo pole, pro druhé a tak dále.

Když přetáhnete **vstup (heslo)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> Pokud vaše aplikace přenáší uživatelská jména a hesla, měli byste nakonfigurovat web tak, aby k šifrování přenosu používal ssl (Secure Sockets Layer). Další informace naleznete v tématu [Zabezpečení připojení](/previous-versions/tn-archive/bb418917(v=technet.10)). Dále je doporučeno ověřit všechny vstupy uživatele. Další informace naleznete [v tématu Ověřování vstupu uživatele v ASP.NET webech webových stránek (Razor).](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Vstup (zaškrtávací políčko)**

![Možnost zaškrtávacího políčka panelu nástrojů webové stránky HTML](../../ide/reference/media/vxcheckbox.gif)

Vloží `input` prvek . `type="checkbox"` Chcete-li změnit zobrazený text, `name` upravte vlastnost. Ve výchozím `id="Checkbox1"` nastavení je vložen pro `id="Checkbox2"` první zaškrtávací políčko, pro druhé a tak dále.

Když přetáhnete **input (zaškrtávací políčko)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**Vstup (rádio)**

![VisualStudioHTMLpageRadioButton – snímek obrazovky](../../ide/reference/media/vxradio.gif)

Vloží `input` prvek . `type="radio"` Chcete-li změnit zobrazený text, `name` upravte vlastnost. Ve výchozím `id="Radio1"` nastavení je vložen pro `id="Radio2"` první přepínací tlačítko, pro druhé a tak dále.

Když přetáhnete **vstup (Rádio)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="Radio1" type="radio" name="Radio1">
```

**Vstup (skrytý)**

![Skrytá položka stránky HTML](../../ide/reference/media/vxhidden.gif)

Vloží `input` prvek . `type="hidden"` Ve výchozím `id="Hidden1"` nastavení je vložen pro `id="Hidden2"` první skryté pole, pro druhé a tak dále.

Když přetáhnete **vstup (Skrytý)** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**Textové pole**

![Textová oblast panelu nástrojů HTMLpage](../../ide/reference/media/vxtextarea.gif)

Vloží `textarea` prvek. Můžete změnit velikost textové oblasti nebo pomocí posuvníků zobrazit text, který přesahuje oblast zobrazení. Chcete-li změnit výchozí zobrazený text, upravte `value` atribut. Ve výchozím `id="textarea1"` nastavení je vložena `id=" textarea 2"` první textová oblast pro druhou a tak dále.

Když přetáhnete **Textarea** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea>
```

> [!IMPORTANT]
> Doporučujeme ověřit všechny vstupy uživatele. Další informace naleznete [v tématu Ověřování vstupu uživatele v ASP.NET webech webových stránek (Razor).](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)

**Table**

![HTMLpageToolbarTable snímek obrazovky](../../ide/reference/media/vxtable.gif)

Vloží `table` prvek.

Když **přetáhnete tabulku** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table>
```

**Obrázek**

![Položka obrázku stránky HTML](../../ide/reference/media/vximage.gif)

Vloží `img` prvek. Upravte tento prvek `src` a `alt` určete jeho a jeho text.

Když **přetáhnete obraz** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<img alt="" src="">
```

**Vybrat**

![Rozevírací seznam nástrojů stránky HTML](../../ide/reference/media/vxdropdown.gif)

Vloží rozevírací `select` prvek (bez atributu). `size` Ve výchozím `id="select1"` nastavení je vložen pro `id="select2"` první seznam, pro druhý a tak dále.

Když přetáhnete **Select** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<select id="select1" name="select1"><option selected></option></select>
```

Víceřádkový `select` prvek můžete vytvořit zvýšením hodnoty vlastnosti size.

**Vodorovné pravidlo**

![Vodorovná položka pravidla stránky HTML](../../ide/reference/media/vxhorizontal.gif)

Vloží `hr` prvek. Chcete-li zvýšit tloušťku čáry, upravte `size` atribut.

Když přetáhnete **vodorovnou pravidlo** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<hr width="100%" size=1>
```

**Div**

![Popisek stránky HTML](../../ide/reference/media/vxlabel.gif)

Vloží `div` prvek, který `ms_positioning="FlowLayout"` obsahuje atribut. S výjimkou šířky a výšky je tato položka shodná s panelem Rozložení toku. Chcete-li formátovat text obsažený `div` v prvku, přidejte `class="stylename"` atribut do počáteční značky.

Když přetáhnete **Div** na povrch návrhového pohledu, do dokumentu se vloží značky HTML, jako je následující:

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>Viz také

- [Sada nástrojů](../../ide/reference/toolbox.md)
