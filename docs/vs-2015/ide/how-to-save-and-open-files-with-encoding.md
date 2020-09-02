---
title: 'Postupy: ukládání a otevírání souborů s kódováním | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Unicode, bi-directional language support
- files, encoding
- bi-directional language support, encoded files
- file encoding, bi-directional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b9285a72137e4c2f3bdf54ef9f6535dedaa2cd5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670781"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Postupy: Ukládání a otevírání souborů se šifrováním
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete ukládat soubory s konkrétním kódováním znaků pro podporu obousměrných jazyků. Můžete také zadat kódování při otevírání souboru, aby aplikace Visual Studio správně zobrazila soubor.

### <a name="to-save-a-file-with-encoding"></a>Uložení souboru s kódováním

1. V nabídce **soubor** zvolte možnost **Uložit soubor jako**a pak klikněte na tlačítko rozevíracího seznamu vedle tlačítka **Uložit** .

     Zobrazí se dialogové okno **Upřesnit možnosti uložení** .

2. V části **kódování**vyberte kódování, které chcete pro soubor použít.

3. V případě potřeby můžete v části **konce řádků**vybrat formát znaků konce řádku.

     Tato možnost je užitečná, pokud máte v úmyslu vyměňovat si soubor s uživateli s jiným operačním systémem.

     Chcete-li pracovat se souborem, který znáte, je kódován určitým způsobem, můžete aplikaci Visual Studio sdělit, aby při otevírání souboru používala toto kódování. Použitá metoda závisí na tom, zda je soubor součástí projektu.

### <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Otevření kódovaného souboru, který je součástí projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor a vyberte možnost **otevřít v programu**.

2. V dialogovém okně **otevřít v aplikaci** vyberte editor, ve kterém se má soubor otevřít.

     Mnoho editorů sady Visual Studio, jako je například editor formulářů, automaticky rozpozná kódování a otevře soubor odpovídajícím způsobem. Pokud zvolíte editor, který umožňuje zvolit kódování, zobrazí se dialogové okno **kódování** .

3. V dialogovém okně **kódování** vyberte kódování, které má Editor použít.

### <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Otevření kódovaného souboru, který není součástí projektu

1. V nabídce **soubor** přejděte na příkaz **otevřít**, zvolte **soubor** nebo **soubor z webu**a potom vyberte soubor, který chcete otevřít.

2. Klikněte na tlačítko rozevíracího seznamu vedle tlačítka **otevřít** a vyberte možnost **otevřít v programu**.

3. Postupujte podle kroků 2 a 3 z předchozího postupu.

## <a name="see-also"></a>Viz také
 [Kódování a model Windows Forms globalizace](https://msdn.microsoft.com/library/22e8965d-a712-42b3-8167-3ee346bd70f9) [a lokalizace aplikací](../ide/globalizing-and-localizing-applications.md)
