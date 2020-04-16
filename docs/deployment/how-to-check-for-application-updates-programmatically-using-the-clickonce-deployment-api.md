---
title: Automatické aktualizace aplikací pomocí rozhraní API pro nasazení ClickOnce
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9300fbf8b348b1016d36d414d17a66c45f6494b9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444614"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Postup: Programově vyhledat aktualizace aplikací pomocí rozhraní API pro nasazení ClickOnce
ClickOnce poskytuje dva způsoby aktualizace aplikace po nasazení. V první metodě můžete nakonfigurovat nasazení ClickOnce automaticky kontrolovat aktualizace v určitých intervalech. Ve druhé metodě můžete napsat kód, který používá třídu <xref:System.Deployment.Application.ApplicationDeployment> ke kontrole aktualizací na základě události, jako je například požadavek uživatele.

 Následující postupy ukazují některé kódy pro provádění programové aktualizace a také popisují, jak nakonfigurovat nasazení ClickOnce pro povolení kontroly programových aktualizací.

 Chcete-li aktualizovat aplikaci ClickOnce programově, musíte zadat umístění aktualizací. To se někdy označuje jako zprostředkovatel nasazení. Další informace o nastavení této vlastnosti naleznete v [tématu Volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Můžete také použít techniku popsanou níže k nasazení aplikace z jednoho umístění, ale aktualizovat z jiného. Další informace naleznete v [tématu Postup: Určení alternativního umístění pro aktualizace nasazení](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Chcete-li vyhledat aktualizace programově

1. Vytvořte novou aplikaci Windows Forms pomocí upřednostňovaného příkazového řádku nebo vizuálních nástrojů.

2. Vytvořte libovolné tlačítko, položku nabídky nebo jinou položku uživatelského rozhraní, kterou mají uživatelé vybrat ke kontrole aktualizací. Z obslužné rutiny události této položky volejte následující metodu ke kontrole a instalaci aktualizací.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Zkompilujte aplikaci.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Použití programu Mage.exe k nasazení aplikace, která programově kontroluje aktualizace

- Postupujte podle pokynů pro nasazení aplikace pomocí mage.exe, jak je vysvětleno v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Při volání Mage.exe ke generování manifestu nasazení nezapomeňte použít `providerUrl`přepínač příkazového řádku a určit adresu URL, kde clickonce by měl zkontrolovat aktualizace. Pokud vaše aplikace `http://www.adatum.com/MyApp`bude aktualizovat z , například volání ke generování manifestu nasazení může vypadat takto:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Použití programu MageUI.exe k nasazení aplikace, která programově kontroluje aktualizace

- Postupujte podle pokynů pro nasazení aplikace pomocí mage.exe, jak je vysvětleno v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Na kartě **Možnosti nasazení** nastavte pole **Počáteční umístění** na manifest aplikace, který by měl ClickOnce vyhledat aktualizace. Na kartě **Možnosti aktualizace** zrušte zaškrtnutí políčka **Tato aplikace by měla zaškrtnout políčko Aktualizace.**

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework
 Aplikace musí mít oprávnění s plnou důvěryhodností, aby mohla používat programové aktualizace.

## <a name="see-also"></a>Viz také
- [Postup: Určení alternativního umístění pro aktualizace nasazení](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)