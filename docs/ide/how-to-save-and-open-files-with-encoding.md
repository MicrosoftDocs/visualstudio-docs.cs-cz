---
title: 'Postupy: ukládání a otevírání souborů s kódováním'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6298e603589d41a6a082b6fe2c1916b3cf8a2a84
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31943056"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Postupy: ukládání a otevírání souborů s kódováním

Soubory lze ukládat s konkrétní znakem kódování pro podporu obousměrných jazycích. Můžete také zadat kódování při otevírání souboru, takže Visual Studio zobrazí soubor správně.

## <a name="to-save-a-file-with-encoding"></a>Uložte soubor s kódováním

1.  Z **soubor** nabídce zvolte **uložit soubor jako**a potom klikněte na tlačítko rozevíracího seznamu vedle položky **Uložit** tlačítko.

     **Rozšířené možnosti ukládání** se zobrazí dialogové okno.

2.  V části **kódování**, vyberte kódování použité pro soubor.

3.  Volitelně můžete v části **konce řádků,**, vyberte formát pro konec řádku znaků.

     Tato možnost je užitečná, pokud máte v úmyslu exchange soubor s uživateli z jiného operačního systému.

     Pokud chcete pracovat s soubor, který víte, že je zakódován do určitým způsobem, můžete zadat, chcete-li používat kódování při otevírání souboru Visual Studio. Metodu, kterou používáte závisí na tom, jestli soubor je součástí projektu.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Chcete-li otevřít kódovaný soubor, který je součástí projektu

1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor a vyberte možnost **otevřít v**.

2.  V **otevřete s** dialogovém okně vyberte editoru otevřete soubor s.

     Mnohé editory Visual Studio, jako je například editor formulářů, bude automaticky rozpoznat kódování a soubor otevřít správně. Pokud se rozhodnete editor, který umožňuje vybrat kódování, **kódování** se zobrazí dialogové okno.

3.  V **kódování** dialogovém okně vyberte kódování, kterou by měla použít editor.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Chcete-li otevřít kódovaný soubor, který není součástí projektu

1.  Na **soubor** nabídky, přejděte na příkaz **otevřete**, zvolte **soubor** nebo **souborů z webové**a pak vyberte příslušný soubor otevřít.

2.  Klikněte na tlačítko rozevíracího seznamu vedle položky **otevřete** tlačítko a zvolte **otevřít v**.

3.  Postupujte podle kroků 2 a 3 v předchozím postupu.

## <a name="see-also"></a>Viz také

- [Kódování a zalomení řádků](encodings-and-line-breaks.md)
- [Globalizace kódování a systém Windows Forms](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)