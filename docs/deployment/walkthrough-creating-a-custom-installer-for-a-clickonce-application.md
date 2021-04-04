---
title: Vytvoření vlastního instalačního programu pro aplikaci ClickOnce
description: Zjistěte, jak může vlastní instalační program tiše nainstalovat a aktualizovat aplikaci ClickOnce založenou na souboru. exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7ae131026a94fa368d55bad1d8cd2164b6f960b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216927"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Návod: Vytvoření vlastního instalačního programu pro aplikaci ClickOnce
Jakoukoli aplikaci ClickOnce založenou na souboru *. exe* lze tiše nainstalovat a aktualizovat pomocí vlastního instalačního programu. Vlastní instalační program může implementovat vlastní uživatelské prostředí během instalace, včetně vlastních dialogových oken pro operace zabezpečení a údržby. K provedení operací instalace používá vlastní instalační program <xref:System.Deployment.Application.InPlaceHostingManager> třídu. Tento návod ukazuje, jak vytvořit vlastní instalační program, který tiše nainstaluje aplikaci ClickOnce.

## <a name="prerequisites"></a>Požadavky

### <a name="to-create-a-custom-clickonce-application-installer"></a>Vytvoření vlastního instalačního programu aplikace ClickOnce

1. V aplikaci ClickOnce přidejte odkazy na System. Deployment a System. Windows. Forms.

2. Přidejte do své aplikace novou třídu a zadejte libovolný název. Tento návod používá název `MyInstaller` .

3. `Imports` `using` Do horní části nové třídy přidejte následující direktivy nebo.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Přidejte následující metody do třídy.

     Tyto metody volají <xref:System.Deployment.Application.InPlaceHostingManager> metody pro stažení manifestu nasazení, vyhodnocení odpovídajících oprávnění, požádejte uživatele o oprávnění k instalaci a pak stáhněte a nainstalujte aplikaci do mezipaměti ClickOnce. Vlastní instalační program může určit, že aplikace ClickOnce je předem důvěryhodná, nebo může odložit rozhodnutí o vztahu důvěryhodnosti s <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> voláním metody. Tento kód předběžně důvěřuje aplikaci.

    > [!NOTE]
    > Oprávnění přiřazená předběžnou důvěryhodností nemůžou přesáhnout oprávnění vlastního kódu instalačního programu.

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs" id="Snippet1":::

5. Chcete-li se pokusit o instalaci z kódu, zavolejte `InstallApplication` metodu. Například pokud jste pojmenovali vaši třídu `MyInstaller` , může zavolat `InstallApplication` následující způsob.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Další kroky
 Aplikace ClickOnce může také přidat vlastní logiku aktualizace, včetně vlastního uživatelského rozhraní, které se má zobrazit během procesu aktualizace. Další informace naleznete v tématu <xref:System.Deployment.Application.UpdateCheckInfo>. Aplikace ClickOnce může také potlačit standardní položky nabídky Start, zástupce a přidat nebo odebrat programy pomocí `<customUX>` elementu. Další informace naleznete v tématu [ \<entryPoint> element](../deployment/entrypoint-element-clickonce-application.md) a <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .

## <a name="see-also"></a>Viz také
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<entryPoint> objekt](../deployment/entrypoint-element-clickonce-application.md)
