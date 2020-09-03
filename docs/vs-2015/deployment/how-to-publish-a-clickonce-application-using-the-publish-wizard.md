---
title: 'Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ff519416d874462a86f7e615822d15139fc4726
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697633"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li aplikaci ClickOnce zpřístupnit uživatelům, je nutné ji publikovat do sdílené složky nebo cesty, serveru FTP nebo na vyměnitelné médium. Aplikaci můžete publikovat pomocí Průvodce publikováním. Další vlastnosti týkající se publikování jsou k dispozici na stránce **publikovat** v **Návrháři projektu**. Další informace naleznete v tématu [publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md).  
  
 Před spuštěním Průvodce publikováním byste měli správně nastavit vlastnosti publikování. Například pokud chcete určit klíč k podepsání aplikace ClickOnce, můžete tak učinit na stránce **podepisování** v **Návrháři projektu**. Další informace najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
> Při instalaci více než jedné verze aplikace pomocí technologie ClickOnce instalační program přesune předchozí verze aplikace do složky s názvem Archive v umístění pro publikování, které zadáte. Archivace předchozích verzí tímto způsobem udržuje instalační adresář v nejasnosti od předchozí verze.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na položku **Nastavení importu a exportu** v nabídce **nástroje** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-publish-to-a-file-share-or-path"></a>Publikování do sdílené složky nebo cesty  
  
1. V **Průzkumník řešení**vyberte projekt aplikace.  
  
2. V nabídce **sestavení** klikněte na **publikovat** `Projectname` .  
  
    Zobrazí se Průvodce publikováním.  
  
3. Na stránce **kde chcete publikovat aplikaci?** zadejte platnou adresu serveru FTP nebo platnou cestu k souboru pomocí jednoho z uvedených formátů a potom klikněte na tlačítko **Další**.  
  
4. Na stránce **jak budou uživatelé aplikaci instalovat?** vyberte umístění, kam budou uživatelé instalovat aplikaci:  
  
   - Pokud budou uživatelé instalovat z webu, klikněte na **z** webu a zadejte adresu URL, která odpovídá cestě k souboru zadané v předchozím kroku. Klikněte na **Next** (Další). (Tato možnost se obvykle používá, když jako umístění pro publikování zadáte adresu FTP. Přímé stahování z FTP serveru se nepodporuje. Proto je třeba zadat adresu URL zde.)  
  
   - Pokud budou uživatelé instalovat aplikaci přímo ze sdílené složky, klikněte na možnost **z cesty UNC nebo sdílené složky**a potom klikněte na tlačítko **Další**. (Toto je pro umístění publikování formuláře c:\deploy\myapp nebo \\ \server\myapp.).  
  
   - Pokud budou uživatelé instalovat z vyměnitelných médií, klikněte na možnost **z disku CD-ROM nebo DVD-ROM**a potom klikněte na tlačítko **Další**.  
  
5. Na stránce **bude aplikace k dispozici offline?** klikněte na příslušnou možnost:  
  
   - Pokud chcete povolit spuštění aplikace v případě odpojení uživatele od sítě, klikněte na **Ano, tato aplikace bude k dispozici online nebo offline**. Pro aplikaci se vytvoří zástupce v nabídce **Start** .  
  
   - Chcete-li spustit aplikaci přímo z umístění publikování, klikněte na tlačítko **Ne, tato aplikace je k dispozici pouze online**. Zástupce v nabídce **Start** nebude vytvořen.  
  
     Pokračujte kliknutím na **Next** (Další).  
  
6. Kliknutím na tlačítko **Dokončit** publikujte aplikaci.  
  
    Stav publikování se zobrazí v oznamovací oblasti stavu.  
  
### <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Publikování na disk CD-ROM nebo DVD-ROM  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt aplikace a klikněte na **vlastnosti**.  
  
    Zobrazí se **Návrhář projektu** .  
  
2. Kliknutím na kartu **publikovat** otevřete stránku **publikovat** v **Návrháři projektu**a klikněte na tlačítko **Průvodce publikováním** .  
  
    Zobrazí se Průvodce publikováním.  
  
3. Na stránce **kde chcete publikovat aplikaci?** zadejte cestu k souboru nebo umístění serveru FTP, kde bude aplikace publikována, například d:\deploy. Pokračujte kliknutím na tlačítko **Další** .  
  
4. Na stránce **jak budou uživatelé aplikaci instalovat?** klikněte na možnost z **disku CD-ROM nebo DVD-ROM**a potom klikněte na tlačítko **Další**.  
  
   > [!NOTE]
   > Pokud chcete, aby se instalace automaticky spustila při vložení disku CD-ROM do jednotky, otevřete stránku **publikovat** v **Návrháři projektu** a klikněte na tlačítko **Možnosti** a potom v průvodci **publikováním možností** vyberte možnost **pro instalaci CD, automaticky spustit instalační program při vložení disku CD**.  
  
5. Pokud distribuujete aplikaci na disk CD-ROM, možná budete chtít poskytnout aktualizace z webu. Na stránce **kde bude aplikace vyhledávat aktualizace?** vyberte možnost aktualizace:  
  
   - Pokud aplikace bude vyhledávat aktualizace, klikněte na **aplikaci vyhledat aktualizace z následujícího umístění** a zadejte umístění, kam budou odesílány aktualizace. Může to být umístění souboru, web nebo FTP server.  
  
   - Pokud aplikace nebude vyhledávat aktualizace, klikněte na aplikace nebude **kontrolovat aktualizace**.  
  
     Pokračujte kliknutím na **Next** (Další).  
  
6. Kliknutím na tlačítko **Dokončit** publikujte aplikaci.  
  
    Stav publikování se zobrazí v oznamovací oblasti stavu.  
  
   > [!NOTE]
   > Po dokončení publikování budete muset ke zkopírování souborů z umístění zadaného v kroku 3 na médium CD-ROM nebo DVD-ROM použít příkaz CD-Write nebo DVD-Write.  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Nasazení řešení Office s použitím technologie ClickOnce](https://msdn.microsoft.com/library/feb516b3-5e4d-449a-9fd2-347d08d90252)
