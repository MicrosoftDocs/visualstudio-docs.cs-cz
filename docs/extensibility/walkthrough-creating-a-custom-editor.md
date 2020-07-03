---
title: 'Návod: Vytvoření vlastního editoru | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4713931d70fd91dd57b85bc6fc749e62e03eb20b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905924"
---
# <a name="walkthrough-create-a-custom-editor"></a>Návod: Vytvoření vlastního editoru
Šablona projektu VSPackage může vytvořit jednoduchý vlastní editor v jazyce C++. Šablona projektu VSPackage již nepodporuje projekty C# nebo Visual Basic. Další informace najdete v tématu [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sadu Visual Studio SDK. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Šablona projektu balíčku sady Visual Studio
 Šablonu projektu balíčku sady Visual Studio najdete v dialogovém okně **Nový projekt** ve složce **rozšiřitelnost C++** .

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Vytvoření VSPackage pomocí šablony balíčku sady Visual Studio

1. Vytvořte projekt pomocí šablony balíčku sady Visual Studio.

2. Vyberte možnost **vlastní editor** a klikněte na tlačítko **Další**. Zobrazí se stránka **Možnosti editoru** .

3. Do pole **název editoru** zadejte název svého editoru. Do pole **Přípona souboru** zadejte příponu souboru, kterou chcete přidružit k vašemu editoru. Editor je k dispozici pro soubory s tímto rozšířením. Přípona souboru je zaregistrována pouze pro aplikaci Visual Studio, nikoli pro systém Windows. Do pole **výchozí název souboru** zadejte výchozí název souboru pro nové dokumenty vytvořené pomocí editoru.

4. Kliknutím na tlačítko **Dokončit** vytvořte VSPackage ve složce, kterou jste určili.

### <a name="to-test-your-custom-editor"></a>Testování vlastního editoru

1. V nabídce **soubor** přejděte na příkaz **Nový** a poté klikněte na možnost **soubor**.

2. V podokně **Nainstalované šablony** v dialogovém okně **nový soubor** vyberte šablonu souboru a potom typ souboru, který jste zaregistrovali.

3. Kliknutím na **otevřít** můžete dokument zobrazit a upravit.

     Editor podporuje operace vyjmutí a vložení, hledání a nahrazení a operací otevřít a načíst.

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
