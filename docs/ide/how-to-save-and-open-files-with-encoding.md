---
title: 'Postupy: ukládání a otevírání souborů s kódováním'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1e562771567a6ff4f9dc35c9e98ceb5441a074
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596174"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Postupy: ukládání a otevírání souborů s kódováním

Můžete ukládat soubory s konkrétním kódováním znaků pro podporu obousměrných jazyků. Můžete také zadat kódování při otevírání souboru, aby aplikace Visual Studio správně zobrazila soubor.

## <a name="to-save-a-file-with-encoding"></a>Uložení souboru s kódováním

1. V nabídce **soubor** zvolte možnost **Uložit soubor jako**a pak klikněte na tlačítko rozevíracího seznamu vedle tlačítka **Uložit** .

     Zobrazí se dialogové okno **Upřesnit možnosti uložení** .

2. V části **kódování**vyberte kódování, které chcete pro soubor použít.

3. V případě potřeby můžete v části **konce řádků**vybrat formát znaků konce řádku.

     Tato možnost je užitečná, pokud máte v úmyslu vyměňovat si soubor s uživateli s jiným operačním systémem.

     Chcete-li pracovat se souborem, který znáte, je kódován určitým způsobem, můžete aplikaci Visual Studio sdělit, aby při otevírání souboru používala toto kódování. Použitá metoda závisí na tom, zda je soubor součástí projektu.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Otevření kódovaného souboru, který je součástí projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor a vyberte možnost **otevřít v programu**.

2. V dialogovém okně **otevřít v aplikaci** vyberte editor, ve kterém se má soubor otevřít.

     Mnoho editorů sady Visual Studio, jako je například editor formulářů, automaticky rozpozná kódování a otevře soubor odpovídajícím způsobem. Pokud zvolíte editor, který umožňuje zvolit kódování, zobrazí se dialogové okno **kódování** .

3. V dialogovém okně **kódování** vyberte kódování, které má Editor použít.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Otevření kódovaného souboru, který není součástí projektu

1. V nabídce **soubor** přejděte na příkaz **otevřít**, zvolte **soubor** nebo **soubor z webu**a potom vyberte soubor, který chcete otevřít.

2. Klikněte na tlačítko rozevíracího seznamu vedle tlačítka **otevřít** a vyberte možnost **otevřít v programu**.

3. Postupujte podle kroků 2 a 3 z předchozího postupu.

## <a name="see-also"></a>Viz také:

- [Kódování a zalomení řádků](encodings-and-line-breaks.md)
- [Kódování a model Windows Forms globalizace](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalizace a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)
