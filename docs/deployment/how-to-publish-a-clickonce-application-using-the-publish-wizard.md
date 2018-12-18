---
title: 'Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 890a61290d7606fb2a03ea7aed2c4782e5b69b67
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388860"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Postupy: publikování aplikace ClickOnce pomocí Průvodce publikováním
Pro aplikaci ClickOnce zpřístupnit uživatelům, je nutné ji publikovat na sdílené složce nebo cestu, FTP server nebo vyměnitelná média. Aplikaci můžete publikovat pomocí Průvodce publikováním; Další vlastnosti týkající se publikování jsou k dispozici na **publikovat** stránku **Návrháře projektu**. Další informace najdete v tématu [publikování ClickOnce applications](../deployment/publishing-clickonce-applications.md).

Před spuštěním Průvodce publikováním byste měli odpovídajícím způsobem nastavit vlastnosti publikování. Například pokud chcete určit klíč k podepsání aplikace ClickOnce, můžete tak učinit na **podepisování** stránku **Návrháře projektu**. Další informace najdete v tématu [zabezpečení ClickOnce applications](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> Při instalaci více než jednu verzi aplikace s použitím technologie ClickOnce, instalace přesune starší verze této aplikace do složky s názvem *archivu*, v umístění pro publikování, který zadáte. Archivace dřívějších verzí tímto způsobem udržuje instalační adresář čistý od složek starší verze.

> [!NOTE]
> Dialogová okna a příkazy nabídek, které se zobrazí mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [Resetovat nastavení](../ide/environment-settings.md#reset-settings).

## <a name="to-publish-to-a-file-share-or-path"></a>K publikování do sdílené složky nebo cesta

1. V **Průzkumníka řešení**, vyberte aplikační projekt.

2. Na **sestavení** nabídky, klikněte na tlačítko **publikovat** *Projectname*.

    Zobrazí se Průvodce publikováním.

3. V **kde chcete publikovat aplikaci?** stránce, zadejte platnou adresu serveru FTP nebo platná cesta k souboru pomocí jednoho z formátů zobrazí a pak klikněte na **Další**.

4. V **jak budou uživatelé aplikaci instalovat?** vyberte umístění, odkud budou uživatelé instalovat aplikaci:

   -   Pokud budou uživatelé instalovat z webového serveru, klikněte na tlačítko **z webu** a zadejte adresu URL, která odpovídá cestu souboru zadanou v předchozím kroku. Klikněte na tlačítko **Další**. (Tato možnost se obvykle používá při zadání adresy FTP jako umístění pro publikování. Přímé stažení ze serveru FTP není podporováno. Proto je nutné zadat adresu URL zde.)

   -   Pokud uživatelé nainstalují aplikace přímo ze sdílené složky, klikněte na tlačítko **ze sdílené složky UNC cestu nebo sdílená složka**a potom klikněte na tlačítko **Další**. (To je pro umístění formuláře publikování *c:\deploy\myapp* nebo  *\\\server\myapp*.)

   -   Pokud budou uživatelé instalovat z vyměnitelných médií, klikněte na tlačítko **z disku CD-ROM nebo DVD-ROM**a potom klikněte na tlačítko **Další**.

5. Na **bude aplikace dostupná offline?** klikněte na příslušnou možnost:

   - Pokud chcete povolit spuštění aplikace když je uživatel odpojen od sítě, klikněte na tlačítko **Ano, tato aplikace bude k dispozici online nebo offline**. Zástupce na **Start** nabídky se vytvoří pro aplikaci.

   - Pokud chcete spustit aplikaci přímo z umístění pro publikování, klikněte na tlačítko **Ne, tato aplikace je dostupná pouze online**. Zástupce na **Start** nabídky se nevytvoří.

     Klikněte na tlačítko **Další** pokračujte.

6. Klikněte na tlačítko **Dokončit** publikování aplikace.

    Stav publikování se zobrazí v oznamovací oblasti.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Chcete-li publikovat na disk CD-ROM nebo DVD-ROM

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt aplikace a klikněte na tlačítko **vlastnosti**.

    **Návrháře projektu** se zobrazí.

2. Klikněte na tlačítko **publikovat** karty otevřete **publikovat** stránku **Návrháře projektu**a klikněte na tlačítko **Průvodce publikováním** tlačítko.

    Zobrazí se Průvodce publikováním.

3. V **kde chcete publikovat aplikaci?** stránky, zadejte cestu k souboru nebo umístění FTP, ve kterém aplikace bude publikována, třeba *d:\deploy*. Pak klikněte na tlačítko **Další** pokračujte.

4. Na **jak budou uživatelé aplikaci instalovat?** klikněte na z **CD-ROM nebo DVD-ROM**a potom klikněte na tlačítko **Další**.

   > [!NOTE]
   >  Pokud chcete, aby se instalace spustila automaticky při vložení disku CD-ROM do jednotky, otevřete **publikovat** stránku **Návrháře projektu** a klikněte na tlačítko **možnosti** tlačítko a pak na **možnosti publikování** průvodce, vyberte **pro instalace z CD automaticky spustit instalační program po vložení disku CD**.

5. Pokud distribuujete aplikaci na disku CD-ROM, můžete chtít poskytnout aktualizace z webu. V **kde bude aplikace vyhledávat aktualizace?** stránce, zvolte možnost aktualizace:

   - Pokud aplikace bude vyhledávat aktualizace, klikněte na tlačítko **bude aplikace vyhledávat aktualizace z následujícího umístění** a zadejte umístění, kde budou aktualizace zveřejňovány. To může být umístění souboru, web nebo FTP server.

   - Pokud aplikace nebude kontrolovat aktualizace, klikněte na tlačítko **aplikace nebude kontrolovat aktualizace**.

     Klikněte na tlačítko **Další** pokračujte.

6. Klikněte na tlačítko **Dokončit** publikování aplikace.

    Stav publikování se zobrazí v oznamovací oblasti.

   > [!NOTE]
   >  Po dokončení publikování budete muset použít CD-RW nebo DVD-RW ke zkopírování souborů z umístění zadaného v kroku 3 na médium CD-ROM nebo DVD-ROM.

## <a name="see-also"></a>Viz také:

- [ClickOnce – zabezpečení a nasazení](../deployment/clickonce-security-and-deployment.md)
- [Zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
- [Nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)