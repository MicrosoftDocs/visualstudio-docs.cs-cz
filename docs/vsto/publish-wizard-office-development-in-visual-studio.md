---
title: Průvodce publikováním (vývoj pro Office v sadě Visual Studio)
description: Naučte se, jak můžete použít Průvodce publikováním ke kopírování souborů řešení do zadaného umístění, vytvoření souborů manifestu a vytvoření instalačního programu v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29400e82dcd7b0d5cd9062679610b50bfaab191d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971684"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Průvodce publikováním (vývoj pro Office v sadě Visual Studio)
  Použijte **Průvodce publikováním** ke zkopírování souborů řešení do zadaného umístění, vytvořte soubory manifestu a vytvořte instalační program.

 Chcete-li získat přístup k tomuto průvodci, v nabídce **sestavení** vyberte možnost **publikovat** *řešení*. K **Průvodci publikováním** můžete také získat přístup z **Průzkumník řešení**. Otevřete místní nabídku uzlu projektu a pak zvolte možnost **publikovat**.

 Každá část níže popisuje stránku průvodce.

## <a name="where-do-you-want-to-publish-the-application"></a>Kam chcete aplikaci publikovat?
 **Zadejte umístění pro publikování této aplikace** Požadovanou. Umístění publikování je adresář, ve kterém **Průvodce publikováním** kopíruje soubory řešení, například manifesty, sestavení, dočasný certifikát a další soubory ze sestavení. Musíte mít přístup pro zápis do tohoto adresáře.

 Zadejte umístění jako cestu k disku, sdílenou složku, server FTP nebo adresu URL webu, nebo klikněte na tlačítko **Procházet** a vyhledejte umístění. Cesta může být v těchto formátech:

- Relativní nebo absolutní cesta ve standardním formátu Windows, jako je například *C:\deploy\myapplication* nebo *\MyApplication*.

- Cesta UNC (Universal Naming Convention), například *\\ \ServerName\MyApplication \\*.

- Adresa URL webu, například `http://www.contoso.com/MyApplication` .

  Ve výchozím nastavení se umístění publikování nachází v případě, že *http://localhost/projectname/* máte nainstalovanou službu IIS, nebo v případě, že nemáte nainstalovanou službu IIS, v adresáři Publish \.

> [!NOTE]
> Pokud cílový počítač používá systém Windows Vista, existuje další informace. Chcete-li použít místní možnost publikování, musíte být správcem počítače se systémem Windows Vista. Kromě toho je výchozí umístění vždy adresář pro *publikování \\* bez ohledu na to, zda je nainstalována služba IIS.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Jaká je výchozí instalační cesta na počítačích koncových uživatelů?
 Instalační cesta je volitelná. Pokud budete chtít, můžete instalační cestu nastavit později. Podrobnosti najdete v tématu [Postup: změna instalační cesty řešení Office](/previous-versions/bb608626(v=vs.110)).

 Instalační cesta je adresář, ze kterého bude koncový uživatel instalovat vlastní nastavení. Je to také cesta, kterou řešení použije ke kontrole aktualizací. **Průvodce publikováním** neimplementuje řešení do tohoto umístění, pokud cesta není stejná jako ta, kterou jste zadali v poli **Zadejte umístění pro publikování této aplikace** na předchozí stránce.

 **Z** webu Zadejte adresu URL, kterou budou koncoví uživatelé postupovat při instalaci řešení.

 **Z cesty UNC nebo sdílené složky** Zadejte cestu UNC, kterou budou koncoví uživatelé postupovat při instalaci řešení.

 **Z disku CD-ROM nebo DVD-ROM** Tato možnost nevyžaduje instalační cestu.

 Visual Studio nevypálí disk CD nebo DVD. Výstup musíte zkopírovat na disk CD nebo DVD ručně.

## <a name="see-also"></a>Viz také
- [Nasazení řešení Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Publikování stránky, Návrháře projektu &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)