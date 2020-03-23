---
title: Možnosti, Textový editor, HTML (webové formuláře), ověření
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ede4600cb1fa1df118b4635a193d8bff348d5119
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568279"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Možnosti, Textový editor, HTML (webové formuláře), ověření

Na stránce **Možnosti ověření** můžete nastavit předvolby, jak editor HTML kontroluje syntaxi značek HTML v dokumentu. Chcete-li získat přístup k této stránce, zvolte na řádku nabídek**možnostI** **nástroje** > a potom rozbalte ověření HTML > **(Webové formuláře)** >  **textového****editoru**( Web .

## <a name="validation"></a>Ověřování

- **Použití doctype pro ověření schématu**

   Schéma určuje, které prvky, atributy a velká písmena jsou platné v tomto schématu. Určuje také značky a atributy, které jsou k dispozici v systému IntelliSense.

   Tuto možnost vyberte, pokud chcete, aby Visual Studio používalo obsah **< stránky! DOCTYPE>** deklarace a **html** element k určení schématu. Pokud například vyberete tuto možnost a `<!DOCTYPE html>`stránka obsahuje deklaraci , použije visual studio schéma HTML5. Pokud má však značka **html** atribut **xmlns,** například `<html xmlns="http://www.w3.org/1999/xhtml">`, visual studio používá schéma XHTML5.

- **Cíl, když nebyl nalezen žádný doctype**

   Vyberte schéma, které chcete ověřit, když není **<! Deklarace>na** stránce.

  - **Zobrazit chyby**

     Chcete-li povolit ověření, zaškrtněte políčko. Pokud toto políčko není zaškrtnuté, editor neoznačí chyby ověření.

     Ostatní zaškrtávací políčka umožňují doladit ověření zadáním jednotlivých typů chyb, které má editor označit.

     > [!NOTE]
     > Některá schémata nenabízejí možnosti označit jednotlivé typy chyb. Pokud například jako cílové schéma zvolíte **XHTML 1.1,** budou všechna zaškrtávací políčka možností zakázána. V tomto případě jsou označeny všechny typy chyb.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
