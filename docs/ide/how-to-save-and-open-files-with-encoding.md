---
title: 'Postup: Ukládání a otevírání souborů pomocí kódování'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596174"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Postup: Ukládání a otevírání souborů pomocí kódování

Můžete ukládat soubory s určitým kódováním znaků pro podporu obousměrných jazyků. Můžete také určit kódování při otevírání souboru, aby visual studio zobrazí soubor správně.

## <a name="to-save-a-file-with-encoding"></a>Uložení souboru s kódováním

1. V nabídce **Soubor** zvolte **Uložit soubor jako**a potom klepněte na rozevírací tlačítko vedle tlačítka **Uložit.**

     Zobrazí se dialogové okno **Upřesnit možnosti uložení.**

2. V části **Kódování**vyberte kódování, které se má pro soubor použít.

3. Volitelně v části **Koncovky řádků**vyberte formát znaků konce řádku.

     Tato možnost je užitečná, pokud máte v úmyslu vyměňovat soubor s uživateli jiného operačního systému.

     Pokud chcete pracovat se souborem, o kterém víte, že je zakódován určitým způsobem, můžete aplikaci Visual Studio říct, aby toto kódování používalo při otevírání souboru. Metoda, kterou použijete, závisí na tom, zda je soubor součástí projektu.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Otevření kódovaného souboru, který je součástí projektu

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor a zvolte **Otevřít pomocí**.

2. V dialogovém okně **Otevřít v akci** zvolte editor, se kterým chcete soubor otevřít.

     Mnoho editorů sady Visual Studio, například editor formulářů, automaticky detekuje kódování a odpovídajícím způsobem otevře soubor. Pokud zvolíte editor, který vám umožní zvolit kódování, zobrazí se dialogové okno **Kódování.**

3. V dialogovém okně **Kódování** vyberte kódování, které má editor používat.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Otevření kódovaného souboru, který není součástí projektu

1. V nabídce **Soubor** přejděte na **Otevřít**, zvolte **Soubor** nebo Soubor **z webu**a pak vyberte soubor, který chcete otevřít.

2. Klikněte na rozevírací tlačítko vedle tlačítka **Otevřít** a zvolte **Otevřít v .**

3. Postupujte podle kroků 2 a 3 z předchozího postupu.

## <a name="see-also"></a>Viz také

- [Kódování a zalomení řádků](encodings-and-line-breaks.md)
- [Kódování a globalizace forem Windows](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globalizace a lokalizaci aplikací](../ide/globalizing-and-localizing-applications.md)
