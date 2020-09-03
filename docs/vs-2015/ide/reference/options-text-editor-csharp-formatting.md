---
title: Možnosti, textový editor, C#, formátování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5371b7180aed462910a57daeb9bf5d43f2ecfedb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662290"
---
# <a name="options-text-editor-c-formatting"></a>Možnosti, textový editor, C#, formátování
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dialogové okno Stránka vlastností **formátování** slouží k nastavení možností formátování kódu v editoru kódu. Chcete-li získat přístup k tomuto dialogovému oknu, klikněte na tlačítko **Možnosti** v nabídce **nástroje** , rozbalte položku **textový editor**, rozbalte položku **C#** a poté klikněte na možnost **formátování**.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="general-settings"></a>Obecná nastavení
 Obecné nastavení ovlivňuje způsob, jakým Editor kódu aplikuje možnosti formátování kódu.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Popisek|Popis|
|-----------|-----------------|
|**Automaticky formátovat dokončený příkaz na;**|Pokud je tato možnost vybrána, formátuje příkazy při dokončení podle možností formátování vybraných pro Editor kódu. Pokud nechcete, aby Editor kódu měnil příkazy, zrušte zaškrtnutí tohoto políčka.|
|**Automaticky formátovat dokončený blok na}**|Je-li vybrána tato možnost, formátuje bloky kódu podle možností formátování vybraných pro Editor kódu ihned po dokončení bloku kódu. Pokud nechcete, aby Editor kódu změnil bloky, zrušte zaškrtnutí tohoto políčka.|
|**Upravit odsazení při vložení**|Když je tato možnost vybrána, formátuje text vložený do editoru kódu, aby odpovídal možnostem formátování vybraným pro Editor kódu. Pokud nechcete, aby se vkládaný text změnil, zrušte zaškrtnutí tohoto políčka.|

## <a name="preview-window"></a>Okno náhledu
 Podokna možností **odsazení**, **nové řádky**, **mezery**a **zalamování** jednotlivých oken zobrazují okno náhledu. V okně náhledu se zobrazí efekt jednotlivých možností. Chcete-li použít okno náhledu, vyberte možnost formátování. V okně náhledu se zobrazí příklad vybrané možnosti. Když změníte nastavení, například když zaškrtnete nebo zrušíte zaškrtnutí políčka, okno náhledu se aktualizuje a zobrazí efekt nového nastavení.

## <a name="remarks"></a>Poznámky
 Možnosti odsazení na stránkách **karet** pro jednotlivé jazyky určují, kde Editor kódu umístí kurzor po stisknutí klávesy ENTER na konci řádku. Možnosti odsazení v části **formátování** platí, pokud je kód automaticky naformátován, například při vložení kódu do souboru, když je vybrána možnost **upravit odsazení při vložení** a když je formátovaný blok zadán ručně.

## <a name="see-also"></a>Viz také
 [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
