---
title: 'Postupy: Správa aktualizací pro aplikaci ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ba899e922e98817462b06a1693525ab1ae69e20
ms.sourcegitcommit: a1e899248adaf104697fa7dea32a36e69e9cc119
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71159906"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Postupy: Správa aktualizací aplikace ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]aplikace mohou vyhledávat aktualizace automaticky nebo programově. Jako vývojář máte spoustu flexibility při určování, kdy a jak se provádějí kontroly aktualizací, jestli jsou aktualizace povinné a kde by měla aplikace vyhledávat aktualizace.

 Aplikaci můžete nakonfigurovat tak, aby kontrolovala aktualizace automaticky před spuštěním aplikace, nebo v nastavených intervalech po spuštění aplikace. Kromě toho můžete zadat minimální požadovanou verzi. To znamená, že je nainstalována aktualizace, pokud je verze uživatele nižší než požadovaná verze.

 Aplikaci můžete nakonfigurovat tak, aby kontrolovala aktualizace programově na základě události, jako je například požadavek uživatele. Postup "vyhledávání aktualizací programově" v tomto tématu ukazuje, jak byste měli napsat kód, který používá <xref:System.Deployment.Application.ApplicationDeployment> třídu ke kontrole aktualizací v závislosti na události.

 Můžete také nasadit aplikaci z jednoho umístění a aktualizovat ji z jiné. Viz Postup určení jiného umístění aktualizace.

 Další informace najdete v tématu [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

 Chování aktualizace je spravováno v dialogovém okně **aktualizace aplikace** , které je k dispozici na stránce **publikovat** v **Návrháři projektu.**

### <a name="to-check-for-updates-before-the-application-starts"></a>Chcete-li vyhledat aktualizace před spuštěním aplikace

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. Klikněte na tlačítko **publikovat** kartu.

3. Kliknutím na tlačítko **aktualizace** otevřete dialogové okno **aktualizace aplikací** .

4. V dialogovém okně **aktualizace aplikace** zkontrolujte, zda je zaškrtnuto políčko **aplikace by měla vyhledat aktualizace** .

5. V části **zvolit, kdy by měla aplikace vyhledávat aktualizace** vyberte **před spuštěním aplikace**. Tím se zajistí, že uživatelé připojení k síti vždy spouštějí aplikaci s nejnovějšími aktualizacemi.

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Zjištění aktualizací na pozadí po spuštění aplikace

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. Klikněte na tlačítko **publikovat** kartu.

3. Kliknutím na tlačítko **aktualizace** otevřete dialogové okno **aktualizace aplikací** .

4. V dialogovém okně **aktualizace aplikace** zkontrolujte, zda je zaškrtnuté políčko **aplikace by měla vyhledávat aktualizace** .

5. V **části zvolit, kdy by měla aplikace vyhledávat aktualizace**vyberte **po spuštění aplikace**. Aplikace začne rychleji tímto způsobem a pak bude kontrolovat aktualizace na pozadí a upozorní uživatele pouze na zpřístupnění aktualizace. Po instalaci se aktualizace projeví až po restartování aplikace.

6. V části **Zadejte, jak často by měla aplikace vyhledávat aktualizace** vyberte buď kontrolovat při **každém spuštění aplikace** (výchozí), nebo **zaškrtněte políčko každých** a zadejte číslo a časový interval.

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Určení minimální požadované verze pro aplikaci

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. Klikněte na tlačítko **publikovat** kartu.

3. Kliknutím na tlačítko **aktualizace** otevřete dialogové okno **aktualizace aplikací** .

4. V dialogovém okně **aktualizace aplikace** zkontrolujte, zda je zaškrtnuto políčko **aplikace by měla vyhledat aktualizace** .

5. Zaškrtněte políčko **zadat minimální požadovanou verzi této aplikace** a potom zadejte čísla **hlavních**, **vedlejších**, **sestavení**a **Revize** pro aplikaci.

### <a name="to-specify-a-different-update-location"></a>Určení jiného umístění aktualizace

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. Klikněte na tlačítko **publikovat** kartu.

3. Kliknutím na tlačítko **aktualizace** otevřete dialogové okno **aktualizace aplikací** .

4. V dialogovém okně **aktualizace aplikace** zkontrolujte, zda je zaškrtnuto políčko **aplikace by měla vyhledat aktualizace** .

5. V poli **umístění aktualizace** zadejte umístění aktualizace s plně kvalifikovanou adresou URL ve formátu *http://Hostname/ApplicationName* nebo cestu UNC pomocí formátu  *\\ \Server\ApplicationName*nebo klikněte na tlačítko **Procházet** a vyhledejte aktualizovat umístění.

### <a name="to-check-for-updates-programmatically"></a>Chcete-li vyhledat aktualizace programově

1. S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.

2. Klikněte na tlačítko **publikovat** kartu.

3. Kliknutím na tlačítko **aktualizace** otevřete dialogové okno **aktualizace aplikací** .

4. V dialogovém okně **aktualizace aplikace** ověřte, zda je zaškrtnuto políčko **aplikace by měla vyhledat aktualizace** . (Volitelně můžete zaškrtnout toto políčko pro kontrolu aktualizací prostřednictvím kódu programu a také umožnění automatického vyhledávání aktualizací ClickOnce.)

5. V poli **umístění aktualizace** zadejte umístění aktualizace s plně kvalifikovanou adresou URL ve formátu *http://Hostname/ApplicationName* nebo cestu UNC pomocí formátu  *\\ \Server\ApplicationName*nebo klikněte na tlačítko **Procházet** a vyhledejte aktualizovat umístění. Umístění aktualizace je místo, kde aplikace bude hledat aktualizovanou verzi sebe sama.

6. Vytvořte tlačítko, položku nabídky nebo jinou položku uživatelského rozhraní ve formuláři Windows, kterou budou uživatelé vybírat pro kontrolu aktualizací. Z obslužné rutiny události této položky zavolejte metodu pro kontrolu a instalaci aktualizací. Příklad Visual Basic a vizuálního C# kódu pro takovou metodu lze nalézt v [tématu How to: Ověřte aktualizace aplikací programově pomocí rozhraní API](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)nasazení ClickOnce.

7. Sestavte aplikaci.

## <a name="see-also"></a>Viz také:
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Dialogové okno aktualizace aplikace](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))
- [Výběr strategie aktualizace ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Postupy: Publikování aplikace ClickOnce pomocí Průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Postupy: Vyhledat aktualizace aplikací programově pomocí rozhraní API nasazení ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
