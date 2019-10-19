---
title: Vytvoření vlastního instalačního programu pro aplikaci ClickOnce
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b648134b7ad27a8f622ce270dc0f05e0a7e6516c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637425"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Návod: Vytvoření vlastního instalačního programu pro aplikaci ClickOnce
Jakoukoli aplikaci ClickOnce založenou na souboru *. exe* lze tiše nainstalovat a aktualizovat pomocí vlastního instalačního programu. Vlastní instalační program může implementovat vlastní uživatelské prostředí během instalace, včetně vlastních dialogových oken pro operace zabezpečení a údržby. K provedení operací instalace používá vlastní instalační program třídu <xref:System.Deployment.Application.InPlaceHostingManager>. Tento návod ukazuje, jak vytvořit vlastní instalační program, který tiše nainstaluje aplikaci ClickOnce.

## <a name="prerequisites"></a>Požadavky

### <a name="to-create-a-custom-clickonce-application-installer"></a>Vytvoření vlastního instalačního programu aplikace ClickOnce

1. V aplikaci ClickOnce přidejte odkazy na System. Deployment a System. Windows. Forms.

2. Přidejte do své aplikace novou třídu a zadejte libovolný název. Tento návod používá název `MyInstaller`.

3. Do horní části nové třídy přidejte následující direktivy `Imports` nebo `using`.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Přidejte následující metody do třídy.

     Tyto metody volají <xref:System.Deployment.Application.InPlaceHostingManager> metody pro stažení manifestu nasazení, vyhodnocení příslušných oprávnění, požádejte uživatele o oprávnění k instalaci a pak stáhněte a nainstalujte aplikaci do mezipaměti ClickOnce. Vlastní instalační program může určit, že aplikace ClickOnce je předem důvěryhodná, nebo může odložit rozhodnutí o vztahu důvěryhodnosti s voláním metody <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>. Tento kód předběžně důvěřuje aplikaci.

    > [!NOTE]
    > Oprávnění přiřazená předběžnou důvěryhodností nemůžou přesáhnout oprávnění vlastního kódu instalačního programu.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Chcete-li se pokusit o instalaci z kódu, zavolejte metodu `InstallApplication`. Například pokud jste jmenovali `MyInstaller` vaší třídy, můžete zavolat `InstallApplication` následujícím způsobem.

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
 Aplikace ClickOnce může také přidat vlastní logiku aktualizace, včetně vlastního uživatelského rozhraní, které se má zobrazit během procesu aktualizace. Další informace najdete v tématu <xref:System.Deployment.Application.UpdateCheckInfo>. Aplikace ClickOnce může také potlačit standardní položky nabídky Start, zástupce a přidat nebo odebrat programy pomocí elementu `<customUX>`. Další informace naleznete v tématu [\<entryPoint > prvek](../deployment/entrypoint-element-clickonce-application.md) a <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>Viz také:
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
- [element \<entryPoint >](../deployment/entrypoint-element-clickonce-application.md)
