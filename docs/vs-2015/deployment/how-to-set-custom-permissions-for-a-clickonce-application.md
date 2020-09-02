---
title: 'Postupy: nastavení vlastních oprávnění pro aplikaci ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6739f38e91ce998441c4cfa62453d485a5d370e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697538"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Postupy: Nastavení vlastních oprávnění pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete nasadit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci, která používá výchozí oprávnění pro zóny Internet nebo místní intranet. Alternativně můžete vytvořit vlastní zónu pro konkrétní oprávnění, která aplikace potřebuje. To lze provést přizpůsobením oprávnění zabezpečení na stránce **zabezpečení** **Návrháře projektu**.  
  
### <a name="to-customize-a-permission"></a>Přizpůsobení oprávnění  
  
1. S projektem vybraným v **Průzkumník řešení**v nabídce **projekt** klikněte na **vlastnosti**.  
  
2. Klikněte na kartu **Zabezpečení**.  
  
3. Zaškrtněte políčko **Povolit nastavení zabezpečení ClickOnce** .  
  
4. Vyberte přepínač možnost **aplikace s částečnou důvěryhodností** .  
  
     Ovládací prvky v oddílu **oprávnění zabezpečení ClickOnce** jsou povolené.  
  
5. Z rozevíracího seznamu zóna, ve které **se aplikace nainstaluje** , klikněte na **(vlastní)**.  
  
6. Klikněte na **Upravit oprávnění XML**.  
  
     Soubor App. manifest se otevře v editoru XML.  
  
7. Před `</applicationRequestMinimum>` element přidejte kód XML pro oprávnění, která vaše aplikace vyžaduje.  
  
    > [!NOTE]
    > Můžete použít `ToXml` metodu sady oprávnění k vygenerování kódu XML pro manifest aplikace. Chcete-li například vygenerovat XML pro <xref:System.Security.Permissions.EnvironmentPermission> sadu oprávnění, zavolejte <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> metodu. Další informace o struktuře XML sady oprávnění naleznete v tématu [NIB: How to: Import sady oprávnění pomocí souboru XML](https://msdn.microsoft.com/dea16b54-c108-408a-ac36-cdc05f746236).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpečení přístupu ke kódu pro aplikace ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
