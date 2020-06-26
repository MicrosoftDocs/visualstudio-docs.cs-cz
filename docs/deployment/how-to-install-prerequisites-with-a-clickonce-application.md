---
title: Jak nainstalovat požadavky pomocí aplikace ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce4ad97439d330a6fc51e741e9ea05ef53a5798a
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382377"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Postupy: Instalace předpokladů s aplikací ClickOnce
Všechny [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace vyžadují, aby byla na počítači nainstalovaná správná verze .NET Framework, aby se mohla spustit; mnoho aplikací má taky další požadavky. Při publikování [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace můžete zvolit sadu požadovaných součástí, které budou zabaleny spolu s vaší aplikací. V době instalace se pro jednotlivé požadavky provede kontrola, aby se zjistilo, jestli už existuje. Pokud není, nainstaluje se před instalací [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace.

 Místo požadavků na balení a publikování můžete také určit umístění pro stahování komponent. Místo toho, abyste museli jako požadavky na každou aplikaci, kterou publikujete, použít například centralizované sdílení souborů nebo webové umístění, které obsahuje instalační programy pro všechny vaše požadavky – v době instalace budou součásti staženy a nainstalovány z tohoto umístění.

> [!IMPORTANT]
> Před publikováním první aplikace byste měli do vývojového počítače přidat požadované instalační balíčky [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Další informace naleznete v tématu [How to: include požadavky s aplikací ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 Požadavky jsou spravovány v dialogovém okně **předpoklady** , přístupné z podokna **publikování** v **Návrháři projektu**.

> [!NOTE]
> Kromě předem vymezeného seznamu požadavků můžete do seznamu přidat vlastní součásti. Další informace najdete v tématu [vytváření balíčků zaváděcího nástroje](../deployment/creating-bootstrapper-packages.md).

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Určení požadavků pro instalaci s aplikací ClickOnce

1. Když je vybrán projekt v **Průzkumník řešení**, v nabídce **projekt** klikněte na **vlastnosti**.

2. Vyberte podokno **publikování** .

3. Kliknutím na tlačítko **požadavky** otevřete dialogové okno **požadavky** .

4. V dialogovém okně **požadavky** se ujistěte, že je zaškrtnuté políčko **vytvořit instalační program pro instalaci požadovaných součástí** .

5. V seznamu **požadavky** zkontrolujte součásti, které chcete nainstalovat, a klikněte na tlačítko **OK**.

     Vybrané součásti budou zabaleny a publikovány spolu s vaší aplikací.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Určení jiného umístění pro stahování pro požadované součásti

1. Když je vybrán projekt v **Průzkumník řešení**, v nabídce **projekt** klikněte na **vlastnosti**.

2. Vyberte podokno **publikování** .

3. Kliknutím na tlačítko **požadavky** otevřete dialogové okno **požadavky** .

4. V dialogovém okně **požadavky** se ujistěte, že je zaškrtnuté políčko **vytvořit instalační program pro instalaci požadovaných součástí** .

5. V části **Zadejte umístění instalace pro požadované součásti** vyberte možnost **Stáhnout požadované součásti z následujícího umístění**.

6. V rozevíracím seznamu vyberte umístění, nebo zadejte adresu URL, cestu k souboru nebo umístění FTP a pak klikněte na **OK.**

    > [!NOTE]
    > Je nutné zajistit, aby v zadaném umístění existovali instalační programy pro zadané součásti.

## <a name="see-also"></a>Viz také
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)