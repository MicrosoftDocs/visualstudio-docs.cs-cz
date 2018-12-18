---
title: 'Postupy: Kontrola aktualizací aplikace programově pomocí rozhraní API nasazení ClickOnce | Dokumentace Microsoftu'
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
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 1a380d549fa10c3229601a1a9541679c7e3ac1e7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282188"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Postupy: Programová kontrola aktualizací aplikace pomocí rozhraní API nasazení ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce poskytuje dva způsoby, jak je nasadíte aktualizaci aplikace. V první metodě můžete nakonfigurovat nasazení ClickOnce, aby automaticky vyhledávat aktualizace v určitých intervalech. Ve druhé metodě můžete napsat kód, který používá <xref:System.Deployment.Application.ApplicationDeployment> třída aktualizace na základě události, jako je například požadavek uživatele.  
  
 Následující postupy ukazují některé kód pro programový aktualizace a také popisují, jak nakonfigurovat nasazení ClickOnce tak, aby povolit kontroly aktualizací prostřednictvím kódu programu.  
  
 Aby bylo možné prostřednictvím kódu programu aktualizuje synchronně aplikaci ClickOnce, je nutné zadat umístění pro aktualizace. To se někdy označuje jako zprostředkovatel nasazení. Další informace o nastavení této vlastnosti naleznete v tématu [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Můžete také použít techniky popsané níže, aby při nasazování aplikace z jednoho místa, ale její aktualizace z jiného. Další informace najdete v tématu [postupy: určení alternativního umístění pro aktualizace nasazení](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Kontrolu aktualizací prostřednictvím kódu programu  
  
1.  Vytvoření nové aplikace Windows Forms pomocí oblíbených nástrojů příkazového řádku nebo visual.  
  
2.  Vytvoření jakékoli tlačítko, položka nabídky nebo jinou položku uživatelského rozhraní se mají vaši uživatelé k výběru a vyhledat aktualizace. Z obslužné rutiny události danou položku zavolejte následující metodu do kontrolovat a instalovat aktualizace.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3.  Zkompilujte aplikaci.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Použití Mage.exe k nasazení aplikace, která zjišťuje dostupnost aktualizací prostřednictvím kódu programu  
  
-   Postupujte podle pokynů pro nasazení aplikace pomocí Mage.exe, jak je vysvětleno v [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Při volání metody Mage.exe ke generování manifestu nasazení, je nutné použít přepínač příkazového řádku `providerUrl`a chcete zadat adresu URL, kde má technologie ClickOnce aktualizace. Pokud vaše aplikace bude aktualizovat z [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), například volání ke generování manifestu nasazení může vypadat takto:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Použití MageUI.exe pro nasazení aplikace, která zjišťuje dostupnost aktualizací prostřednictvím kódu programu  
  
-   Postupujte podle pokynů pro nasazení aplikace pomocí Mage.exe, jak je vysvětleno v [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Na **možnosti nasazení** kartu, nastavte **počáteční umístění** pole do manifestu aplikace ClickOnce by měla vyhledávat aktualizace. Na **možnosti aktualizace** kartu, zrušte **tato aplikace by měla vyhledávat aktualizace** zaškrtávací políčko.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vaše aplikace musí mít oprávnění plné důvěryhodnosti pro použití programových aktualizací.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: určení alternativního umístění pro aktualizace nasazení](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)



