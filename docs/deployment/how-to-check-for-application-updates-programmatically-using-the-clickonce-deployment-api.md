---
title: 'Postupy: Kontrola aktualizací aplikace programově pomocí rozhraní API nasazení ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25585dce22f74c8e8b2f6aef253ea00c3a6ad4e8
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151390"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Postupy: Kontrola aktualizací aplikace programově pomocí rozhraní API nasazení ClickOnce
ClickOnce poskytuje dva způsoby, jak je nasadíte aktualizaci aplikace. V první metodě můžete nakonfigurovat nasazení ClickOnce, aby automaticky vyhledávat aktualizace v určitých intervalech. Ve druhé metodě můžete napsat kód, který používá <xref:System.Deployment.Application.ApplicationDeployment> třída aktualizace na základě události, jako je například požadavek uživatele.  
  
 Následující postupy ukazují některé kód pro programový aktualizace a také popisují, jak nakonfigurovat nasazení ClickOnce tak, aby povolit kontroly aktualizací prostřednictvím kódu programu.  
  
 Aby bylo možné prostřednictvím kódu programu aktualizuje synchronně aplikaci ClickOnce, je nutné zadat umístění pro aktualizace. To se někdy označuje jako zprostředkovatel nasazení. Další informace o nastavení této vlastnosti naleznete v tématu [volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Můžete také použít techniky popsané níže, aby při nasazování aplikace z jednoho místa, ale její aktualizace z jiného. Další informace najdete v tématu [postupy: určení alternativního umístění pro aktualizace nasazení](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Kontrolu aktualizací prostřednictvím kódu programu  
  
1.  Vytvoření nové aplikace Windows Forms pomocí oblíbených nástrojů příkazového řádku nebo visual.  
  
2.  Vytvoření jakékoli tlačítko, položka nabídky nebo jinou položku uživatelského rozhraní se mají vaši uživatelé k výběru a vyhledat aktualizace. Z obslužné rutiny události danou položku zavolejte následující metodu do kontrolovat a instalovat aktualizace.  
  
     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  Zkompilujte aplikaci.  
  
### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Použijte Mage.exe k nasazení aplikace, zjišťuje dostupnost aktualizací prostřednictvím kódu programu  
  
-   Postupujte podle pokynů pro nasazení aplikace pomocí Mage.exe, jak je vysvětleno v [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Při volání metody Mage.exe ke generování manifestu nasazení, je nutné použít přepínač příkazového řádku `providerUrl`a chcete zadat adresu URL, kde má technologie ClickOnce aktualizace. Pokud vaše aplikace bude aktualizovat z [ http://www.adatum.com/MyApp ](http://www.adatum.com/MyApp), například volání ke generování manifestu nasazení může vypadat takto:  
  
    ```cmd 
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Použití MageUI.exe pro nasazení aplikace, která zjišťuje dostupnost aktualizací prostřednictvím kódu programu  
  
-   Postupujte podle pokynů pro nasazení aplikace pomocí Mage.exe, jak je vysvětleno v [návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Na **možnosti nasazení** kartu, nastavte **počáteční umístění** pole do manifestu aplikace ClickOnce by měla vyhledávat aktualizace. Na **možnosti aktualizace** kartu, zrušte **tato aplikace by měla vyhledávat aktualizace** zaškrtávací políčko.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vaše aplikace musí mít oprávnění plné důvěryhodnosti pro použití programových aktualizací.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: určení alternativního umístění pro aktualizace nasazení](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)