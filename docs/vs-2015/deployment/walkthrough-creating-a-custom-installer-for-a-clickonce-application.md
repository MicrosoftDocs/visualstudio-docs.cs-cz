---
title: 'Návod: Vytvoření vlastního instalačního programu pro aplikaci ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ebde75fdf36c84f40ae660a24d469c36e72ceaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821339"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Návod: Vytvoření vlastního instalátoru pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jakoukoli aplikaci ClickOnce založenou na souboru. exe lze tiše nainstalovat a aktualizovat pomocí vlastního instalačního programu. Vlastní instalační program může implementovat vlastní uživatelské prostředí během instalace, včetně vlastních dialogových oken pro operace zabezpečení a údržby. K provedení operací instalace používá vlastní instalační program <xref:System.Deployment.Application.InPlaceHostingManager> třídu. Tento návod ukazuje, jak vytvořit vlastní instalační program, který tiše nainstaluje aplikaci ClickOnce.  
  
## <a name="prerequisites"></a>Předpoklady  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Vytvoření vlastního instalačního programu aplikace ClickOnce  
  
1. V aplikaci ClickOnce přidejte odkazy na System. Deployment a System. Windows. Forms.  
  
2. Přidejte do své aplikace novou třídu a zadejte libovolný název. Tento návod používá název `MyInstaller` .  
  
3. `Imports` `using` Do horní části nové třídy přidejte následující příkazy nebo.  
  
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
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
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
 [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint> Objekt](../deployment/entrypoint-element-clickonce-application.md)
