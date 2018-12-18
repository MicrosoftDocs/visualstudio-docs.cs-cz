---
title: 'Krok 10: Zapište kód pro přídavná tlačítka a zaškrtávací políčko'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a5b7fa7291def4a988d268eebdf9bf5e96c7f7b
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747756"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10: Zapište kód pro přídavná tlačítka a zaškrtávací políčko
Nyní jste připraveni dokončit čtyři metody. Můžete zkopírovat a vložit tento kód, ale pokud chcete získat další využití tohoto kurzu, zadejte kód a použít technologii IntelliSense.

 Tento kód přidá funkce na tlačítka, který jste přidali dříve. Bez tohoto kódu tlačítka není nijak. Tlačítka použít kód v jejich <xref:System.Windows.Forms.Control.Click> události (a používá zaškrtávací políčko <xref:System.Windows.Forms.CheckBox.CheckedChanged> událostí) provádět různé akce při aktivaci ovládacích prvků. Například `clearButton_Click` událost, která aktivuje, když zvolíte **Vymazat obrázek** tlačítko, vymaže aktuální image nastavením jeho **Image** vlastnost **null**(nebo **nic**). Každá událost v kódu obsahuje komentáře, které popisují, co kód dělá.

 ![odkaz na video](../data-tools/media/playvideo.gif)video verzi tohoto tématu naleznete v části [kurzu 1: vytvoření prohlížeče obrázků v jazyce Visual Basic – Video 5](http://go.microsoft.com/fwlink/?LinkId=205216) nebo [kurzu 1: vytvoření prohlížeče obrázků v jazyce C# - Video 5](http://go.microsoft.com/fwlink/?LinkId=205206). Tyto videa pomocí starší verze sady Visual Studio, takže drobné rozdíly v některé příkazy a další prvky uživatelského rozhraní. Však koncepty a postupy fungují podobně jako v aktuální verzi sady Visual Studio.

> [!NOTE]
>  Jako osvědčený postup: vždy komentář ke kódu. Komentáře jsou informace osoby ke čtení a je vhodné čas srozumitelnost kódu. Vše na řádku komentáře je ignorován v programu. V jazyce Visual C# můžete komentář řádku zadáním dvě lomítka na začátku (/ /), a v jazyce Visual Basic komentář řádku od jednoduché uvozovky (').

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Napsat kód pro přídavná tlačítka a zaškrtávací políčko

-   Přidejte následující kód do vaší **Form1** souboru kódu (*Form1.cs* nebo *Form1.vb*). Vyberte **VB** zobrazíte kód jazyka Visual Basic.

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Chcete-li přejít k dalšímu kroku kurzu, přečtěte si téma [krok 11: Spusťte svůj program a vyzkoušejte jiné funkce](../ide/step-11-run-your-program-and-try-other-features.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 9: Zkontrolujte, okomentujte a otestujte svůj kód](../ide/step-9-review-comment-and-test-your-code.md).
