---
title: 'Postupy: Správa aktualizací pro aplikaci ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: adf0a6df54c3e6bd758896ac8a836b6174e767b8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272464"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Postupy: Správa aktualizací pro aplikaci ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace můžete vyhledat aktualizace automaticky, nebo prostřednictvím kódu programu. Jako vývojář máte velké množství flexibilitu při určení, kdy a jak jsou provedeny aktualizace kontroly, zda jsou povinné aktualizace a kde by měla aplikace vyhledávat aktualizace.  
  
 Můžete nakonfigurovat aplikace vyhledávat aktualizace automaticky před spuštěním aplikace nebo v nastavených intervalech po spuštění aplikace. Kromě toho můžete určit minimální požadovaná verze; Pokud uživatele verze je nižší než požadovaná verze je tedy instalována aktualizace.  
  
 Můžete nakonfigurovat aplikace vyhledávat aktualizace prostřednictvím kódu programu na základě události jako je například požadavek uživatele. Postup "programová kontrola aktualizací" v tomto tématu ukazuje, jak byste napsat kód, který používá <xref:System.Deployment.Application.ApplicationDeployment> třída aktualizace na základě události.  
  
 Také můžete nasadit aplikace z jednoho místa a aktualizovat z jiného. Viz procedura "můžete zadat jiné umístění aktualizace."  
  
 Další informace najdete v tématu [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Chování aktualizace se spravuje v **aktualizace aplikace** dialogovém okně k dispozici **publikovat** stránku **Návrháře projektu.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Kontrolu aktualizací před spuštěním aplikace  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **aktualizace** tlačítko Otevřít **aktualizace aplikace** dialogové okno.  
  
4.  V **aktualizace aplikace** dialogové okno pole, ujistěte se, že **by měla aplikace vyhledávat aktualizace** zaškrtávací políčko je zaškrtnuto.  
  
5.  V **Vyberte prosím, kdy by měla aplikace vyhledávat aktualizace** vyberte **před spuštěním aplikace**. Tím se zajistí, že uživatelé připojení k síti vždy spustit aplikaci s nejnovější aktualizací.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Chcete-li vyhledat aktualizace na pozadí po spuštění aplikace  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **aktualizace** tlačítko Otevřít **aktualizace aplikace** dialogové okno.  
  
4.  V **aktualizace aplikace** dialogové okno pole, ujistěte se, že políčko **by měla aplikace vyhledávat aktualizace** zaškrtnuto.  
  
5.  V **Vyberte prosím, kdy by měla aplikace vyhledávat aktualizace části**vyberte **po spuštění aplikace**. Aplikace se spustí rychleji tímto způsobem, a pak bude vyhledávat aktualizace na pozadí a pouze upozornit uživatele, pokud je k dispozici aktualizace. Po instalaci aktualizace se projeví až po restartování aplikace.  
  
6.  V **zadejte, jak často by měla aplikace vyhledávat aktualizace** vyberte buď **zkontrolovat při každém spuštění aplikace** (výchozí) nebo **Zkontrolujte každý** a zadejte číslo a čas intervalu.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Chcete-li určit minimální požadovaná verze aplikace  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **aktualizace** tlačítko Otevřít **aktualizace aplikace** dialogové okno.  
  
4.  V **aktualizace aplikace** dialogové okno pole, ujistěte se, že **by měla aplikace vyhledávat aktualizace** zaškrtávací políčko je zaškrtnuto.  
  
5.  Vyberte **zadat minimální požadovanou verzi této aplikace** zaškrtněte políčko a potom zadejte **hlavní**, **menší**, **sestavení**a  **Revize** čísla pro aplikaci.  
  
### <a name="to-specify-a-different-update-location"></a>Chcete-li zadat jiné umístění aktualizace  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **aktualizace** tlačítko Otevřít **aktualizace aplikace** dialogové okno.  
  
4.  V **aktualizace aplikace** dialogové okno pole, ujistěte se, že **by měla aplikace vyhledávat aktualizace** zaškrtávací políčko je zaškrtnuto.  
  
5.  V **aktualizovat umístění** zadejte umístění aktualizace s plně kvalifikovanou adresu URL pomocí formátu http://Hostname/ApplicationName, nebo cestu UNC ve formátu \\\Server\ApplicationName nebo kliknutím **Procházet** vyhledat umístění aktualizace.  
  
### <a name="to-check-for-updates-programmatically"></a>Kontrolu aktualizací prostřednictvím kódu programu  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **aktualizace** tlačítko Otevřít **aktualizace aplikace** dialogové okno.  
  
4.  V **aktualizace aplikace** dialogové okno pole, ujistěte se, že **by měla aplikace vyhledávat aktualizace** zrušení zaškrtnutí políčka. (Můžete volitelně vybrat toto políčko, chcete-li kontrolovat aktualizace prostřednictvím kódu programu a také nechat ClickOnce aktualizace vyhledávat automaticky.)  
  
5.  V **aktualizovat umístění** zadejte umístění aktualizace s plně kvalifikovanou adresu URL pomocí formátu http://Hostname/ApplicationName, nebo cestu UNC ve formátu \\\Server\ApplicationName nebo kliknutím **Procházet** vyhledat umístění aktualizace. Aktualizace umístění je, ve kterém bude aplikace vyhledávat aktualizovanou verzi sebe sama.  
  
6.  Vytvoření tlačítka, položka nabídky nebo jinou položku uživatelského rozhraní na formuláři Windows, který uživatelé zvolí kontrolu aktualizací. Z této položky obslužné rutiny události zavolejte metodu kontrolovat a instalovat aktualizace. Příklad kódu jazyka Visual Basic a Visual C# najdete metody v [jak: vyhledejte aplikaci aktualizace programově pomocí rozhraní API nasazení ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Sestavení aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Dialogové okno aktualizace aplikace](http://msdn.microsoft.com/en-us/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Postupy: Programová kontrola aktualizací aplikace pomocí rozhraní API nasazení ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)



