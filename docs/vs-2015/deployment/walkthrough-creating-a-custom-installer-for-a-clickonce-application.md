---
title: 'Návod: Vytvoření vlastního instalátoru pro aplikaci ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 16686b0bf53f9e1358d96a7abcfe95f8ed6aac82
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222765"
---
# <a name="walkthrough-creating-a-custom-installer-for-a-clickonce-application"></a>Návod: Vytvoření vlastního instalátoru pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Každá aplikace ClickOnce, na základě souboru .exe jde bezobslužně nainstalovat a aktualizovat vlastní instalační program. Vlastní instalační program můžete implementovat vlastní uživatelské prostředí při instalaci, včetně vlastní dialogová okna pro operace zabezpečení a údržba. K provedení operace instalace, používá vlastní instalační program <xref:System.Deployment.Application.InPlaceHostingManager> třídy. Tento návod ukazuje, jak vytvořit vlastní instalační program, který tiché instalaci aplikace ClickOnce.  
  
## <a name="prerequisites"></a>Požadavky  
  
### <a name="to-create-a-custom-clickonce-application-installer"></a>Chcete-li vytvořit vlastní instalační program aplikace ClickOnce  
  
1.  Ve vaší aplikaci ClickOnce přidejte odkazy na System.Deployment a System.Windows.Forms.  
  
2.  Přidejte novou třídu do vaší aplikace a zadat libovolný název. Tento návod používá název `MyInstaller`.  
  
3.  Přidejte následující `Imports` nebo `using` příkazy k hornímu okraji novou třídu.  
  
    ```vb  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```csharp  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Přidejte následující metody do vaší třídy.  
  
     Tyto metody volat <xref:System.Deployment.Application.InPlaceHostingManager> metody se stáhnout manifest nasazení vyhodnocení příslušná oprávnění, požádat uživatele o oprávnění k instalaci a pak si stáhnout a nainstalovat aplikaci do mezipaměti ClickOnce. Vlastní instalační program můžete určit, že je předem důvěryhodné aplikace ClickOnce, nebo můžete odložit rozhodnutí důvěryhodnosti <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> volání metody. Tento kód předběžně vztahy důvěryhodnosti aplikace.  
  
    > [!NOTE]
    >  Oprávnění přiřazená předem důvěryhodnou nesmí překročit oprávnění kód vlastní instalační služby.  
  
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs#1)]
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb#1)]  
  
5.  Chcete-li se pokusit o instalaci v kódu, zavolejte `InstallApplication` metody. Například pokud pojmenujete vaší třídy `MyInstaller`, může volat `InstallApplication` následujícím způsobem.  
  
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
 Aplikace ClickOnce můžete také přidat logiku vlastních aktualizací, včetně vlastní uživatelské rozhraní zobrazit během procesu aktualizace. Další informace naleznete v tématu <xref:System.Deployment.Application.UpdateCheckInfo>. Aplikace ClickOnce můžete potlačit také standardní položky nabídky Start, zástupce a položky panelu Přidat nebo odebrat programy pomocí `<customUX>` elementu. Další informace najdete v tématu [ \<entryPoint > Element](../deployment/entrypoint-element-clickonce-application.md) a <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – Manifest aplikace](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint > – Element](../deployment/entrypoint-element-clickonce-application.md)



