---
title: 'Návod: Vytvoření vlastního editoru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697671"
---
# <a name="walkthrough-create-a-custom-editor"></a>Návod: Vytvoření vlastního editoru
Šablona projektu VSPackage může vytvořit jednoduchý vlastní editor v jazyce C++. Šablona projektu VSPackage již nepodporuje projekty jazyka C# nebo Visual Basic. Další informace naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Požadavky
 Chcete-li postupovat podle tohoto návodu, je nutné nainstalovat sady Visual Studio SDK. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>Šablona projektu Balíček sady Visual Studio
 Šablonu projektu balíčku sady Visual Studio najdete v dialogovém okně **Nový projekt** ve složce **Rozšiřitelnost jazyka C++.**

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Vytvoření balíčku VSPackage pomocí šablony balíčku sady Visual Studio

1. Vytvořte projekt pomocí šablony balíčku sady Visual Studio.

2. Vyberte možnost **Vlastní editor** a klepněte na tlačítko **Další**. Zobrazí se stránka **Možnosti editoru.**

3. Do pole **Název editoru** zadejte název editoru. Do pole Přípona souboru zadejte příponu souboru, kterou chcete přidružit k editoru, do pole **Přípona souboru.** Editor je k dispozici pro soubory s touto příponou. Přípona souboru je registrována pouze pro Visual Studio, ne pro Windows. Do pole **Výchozí název souboru** zadejte výchozí název souboru pro nové dokumenty vytvořené editorem.

4. Kliknutím na **Dokončit** vytvořte balíček VSPackage ve zadané složce.

### <a name="to-test-your-custom-editor"></a>Testování vlastního editoru

1. V nabídce **Soubor** přejděte na **Nový** a potom klepněte na **příkaz Soubor**.

2. V podokně **Nainstalované šablony** dialogového okna **Nový soubor** vyberte šablonu souboru a pak typ souboru, který jste zaregistrovali.

3. Kliknutím na **Otevřít** dokument zobrazíte a upravíte.

     Editor podporuje operace vyjmutí a vložení, hledání a nahrazování a otevřených a zatěžovacích operací.

## <a name="see-also"></a>Viz také
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
