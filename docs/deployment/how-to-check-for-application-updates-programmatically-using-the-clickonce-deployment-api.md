---
title: Automatické aktualizace aplikací pomocí rozhraní API nasazení ClickOnce
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 6aee738d972b7c6e8c857ae87bb25758d871fe28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382572"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Postupy: vyhledání aktualizací aplikace programově pomocí rozhraní API nasazení ClickOnce
ClickOnce poskytuje dva způsoby, jak aplikaci aktualizovat po nasazení. V první metodě můžete nakonfigurovat nasazení ClickOnce tak, aby v určitých intervalech automaticky kontrolovala aktualizace. Ve druhé metodě můžete napsat kód, který používá <xref:System.Deployment.Application.ApplicationDeployment> třídu ke kontrole aktualizací na základě události, jako je například požadavek uživatele.

 Následující postupy ukazují nějaký kód pro provádění programové aktualizace a také popisují, jak nakonfigurovat nasazení ClickOnce pro povolení programových kontrol aktualizací.

 Aby bylo možné aplikaci ClickOnce aktualizovat programově, je nutné zadat umístění pro aktualizace. Tato situace je někdy označována jako poskytovatel nasazení. Další informace o nastavení této vlastnosti naleznete v tématu [volba strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Můžete také použít techniku popsanou níže pro nasazení aplikace z jednoho umístění, ale aktualizaci z jiné. Další informace najdete v tématu [Postup: určení alternativního umístění pro aktualizace nasazení](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Chcete-li vyhledat aktualizace programově

1. Pomocí preferovaného příkazového řádku nebo vizuálních nástrojů vytvořte novou aplikaci model Windows Forms.

2. Vytvořte libovolné tlačítko, položku nabídky nebo jinou položku uživatelského rozhraní, které chcete, aby uživatelé vybrali, aby zkontrolovali aktualizace. Z obslužné rutiny události této položky zavolejte následující metodu, která zkontroluje a nainstaluje aktualizace.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Zkompilujte aplikaci.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Použití Mage.exe k nasazení aplikace, která kontroluje aktualizace programově

- Postupujte podle pokynů pro nasazení aplikace pomocí Mage.exe, jak je vysvětleno v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Při volání Mage.exe pro vygenerování manifestu nasazení, nezapomeňte použít přepínač příkazového řádku `providerUrl` a zadat adresu URL, kde má ClickOnce vyhledat aktualizace. Pokud se vaše aplikace bude aktualizovat `http://www.adatum.com/MyApp` , například volání vygenerování manifestu nasazení, může vypadat takto:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Použití MageUI.exe k nasazení aplikace, která kontroluje aktualizace programově

- Postupujte podle pokynů pro nasazení aplikace pomocí Mage.exe, jak je vysvětleno v [návodu: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Na kartě **Možnosti nasazení** nastavte pole **počáteční umístění** na manifest aplikace ClickOnce by měl vyhledat aktualizace. Na kartě **Možnosti aktualizace** zrušte zaškrtnutí políčka **Tato aplikace by měla vyhledávat aktualizace** .

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework
 Aby vaše aplikace mohla používat programové aktualizace, musí mít oprávnění úplného vztahu důvěryhodnosti.

## <a name="see-also"></a>Viz také
- [Postupy: určení alternativního umístění pro aktualizace nasazení](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)