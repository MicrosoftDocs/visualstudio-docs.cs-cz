---
title: Výběr fragmentu kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.expansionpicker
helpviewer_keywords:
- Code Snippet Picker
- IntelliSense code snippets, Code Snippet Picker
- code snippets, Code Snippet Picker
ms.assetid: f0862d48-fbbc-4cfe-b228-24492d5c89c4
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2918826d6923efa3db42f4f572c416b9668513a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660889"
---
# <a name="code-snippet-picker"></a>Sběrač fragmentů kódu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Editor kódu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] poskytuje **Výběr fragmentu kódu** , který umožňuje v několika kliknutích myši vkládat připravené bloky kódu do aktivního dokumentu.

 Postup zobrazení **výběru fragmentu kódu** se liší v závislosti na jazyku, který používáte.

- [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] – kliknutím pravým tlačítkem myši na požadované místo v editoru kódu zobrazte místní nabídku a vyberte možnost **Vložit fragment**.

- [!INCLUDE[csprcs](../../includes/csprcs-md.md)] – kliknutím pravým tlačítkem myši na požadované místo v editoru kódu zobrazte místní nabídku a klikněte na příkaz **Vložit fragment** nebo **obklopit pomocí**.

- [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] – **Výběr fragmentu kódu** není k dispozici.

- Vizuál F# – **Výběr fragmentu kódu** není k dispozici.

- [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] – kliknutím pravým tlačítkem myši na požadované místo v editoru kódu zobrazte místní nabídku a klikněte na příkaz **Vložit fragment** nebo **obklopit pomocí**.

- XML – kliknutím pravým tlačítkem myši na požadované místo v editoru kódu zobrazte místní nabídku a klikněte na příkaz **Vložit fragment** nebo **obklopit pomocí**.

- HTML – kliknutím pravým tlačítkem myši na požadované místo v editoru kódu zobrazíte místní nabídku a kliknete na **Vložit fragment** nebo **obklopit s**.

- SQL – kliknutím pravým tlačítkem myši na požadované místo v editoru kódu zobrazíte místní nabídku a kliknete na možnost **Vložit fragment**.

  Ve většině vývojových jazyků sady Visual Studio můžete pomocí **Správce fragmentů kódu** přidat složky do **seznamu složek** , který nástroj pro **Výběr fragmentu kódu** vyhledává soubory fragmentů XML. Můžete také vytvořit vlastní fragmenty kódu, které chcete přidat do seznamu. Další informace naleznete v tématu [Návod: Vytvoření fragmentu kódu](../../ide/walkthrough-creating-a-code-snippet.md).

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní
 Název položky: upravitelné textové pole, které zobrazuje název položky vybrané v **seznamu položek**. Chcete-li provést přírůstkové hledání požadované položky, začněte zadávat název do tohoto pole. Pokračujte v přidávání písmen, dokud není v **seznamu položek**vybraná požadovaná položka.

 Seznam položek: seznam fragmentů kódu, které jsou k dispozici pro vložení, nebo seznam složek obsahující fragmenty kódu. Pokud chcete vložit fragment nebo rozbalit složku, vyberte požadovanou položku a stiskněte klávesu ENTER.

## <a name="see-also"></a>Viz také
 [Osvědčené postupy pro používání fragmentů kódu](../../ide/best-practices-for-using-code-snippets.md) [Visual Basic nastavení záložky technologie IntelliSense](https://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643) [v kódu](../../ide/setting-bookmarks-in-code.md) [Postupy: použití příkazu obklopit s fragmenty kódu](../../ide/how-to-use-surround-with-code-snippets.md)
