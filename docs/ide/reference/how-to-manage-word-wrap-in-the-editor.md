---
title: Zalamování řádků
ms.date: 11/07/2018
ms.topic: how-to
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4bf76643ce1ea6e2f449c54fbc31d441418becf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85770334"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Postupy: Správa zalamování řádků v editoru

Můžete nastavit a vymazat možnost **zalamování slov** . Pokud je tato možnost nastavena, část dlouhé čáry, která přesahuje aktuální šířku okna editoru kódu, se zobrazí na dalším řádku. Pokud je tato možnost prázdná, například pro usnadnění použití číslování řádků, můžete přejít na pravé tlačítko a zobrazit konce dlouhých řádků.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac naleznete v tématu [Editor zdrojového kódu: zalamování řádků](/visualstudio/mac/source-editor#word-wrap).

## <a name="to-set-word-wrap-preferences"></a>Nastavení předvoleb zalamování řádků

1. V nabídce **Tools** (Nástroje) vyberte **Options** (Možnosti).

2. Ve složce **textový editor** výběrem možnosti **Obecné** v podsložce **všechny jazyky** nastavte tuto možnost globálně.

     ani

     V podsložce vyberte **Obecné** možnosti pro jazyk, ve kterém programujete.

3. V části **Nastavení**zaškrtněte nebo zrušte zaškrtnutí políčka **zalamování řádků** .

     Je-li vybrána možnost **zalamování řádků** , možnost **Zobrazit vizuální glyfy pro zalamování řádků** je povolena.

4. Vyberte možnost **Zobrazit vizuální glyfy pro zalamování řádků** , pokud upřednostňujete zobrazení indikátoru pro návratové šipky, kde se dlouhá čára zalomí na druhý řádek. Tuto možnost zrušte, pokud nechcete zobrazovat šipky indikátorů.

    > [!NOTE]
    > Tyto šipky připomenutí nejsou přidány do kódu; jsou jen pro účely zobrazení.

## <a name="known-issues"></a>Známé problémy

Pokud jste obeznámeni se zalamováním řádků v programu Notepad + +, podprogramový text nebo Visual Studio Code, pamatujte na následující problémy, kde se Visual Studio chová jinak než v jiných editorech:

* [Třikrát kliknout na možnost nevybírat celý řádek](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [Stisknutím klávesy END dvakrát nepřesunete kurzor na konec řádku.](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../../ide/writing-code-in-the-code-and-text-editor.md)
