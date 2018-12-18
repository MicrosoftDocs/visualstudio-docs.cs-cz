---
title: 'Postupy: určení souborů k publikování aplikací ClickOnce | Dokumentace Microsoftu'
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
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.File
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, file exclusion
- files, publishing via ClickOnce
ms.assetid: 579c134a-d50f-4e0c-8e05-2a4ff654896a
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2a8d408aa7d7ae04d5ed83c2687ca34ce79e404e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268317"
---
# <a name="how-to-specify-which-files-are-published-by-clickonce"></a>Postupy: Určení souborů k publikování aplikací ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při publikování [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] spolu s aplikace jsou nasazené aplikace, všechny kód soubory v projektu. V některých případech se nemusí nebo potřebujete publikovat určité soubory nebo můžete chtít nainstalovat určité soubory na základě podmínek. Visual Studio umožňuje vyloučit soubory, soubory označit jako datové soubory nebo požadavky a vytvářet skupiny podmíněné instalačním souborům.  
  
 Soubory pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace se spravují v **soubory aplikace** dialogové okno, přístupné **publikovat** stránku **Návrháře projektu**.  
  
 Standardně je skupina jeden soubor s názvem **(povinné)**. Můžete vytvořit další skupiny souborů a k nim přiřadíte soubory. Nelze změnit **skupina pro stažení** pro soubory, které jsou požadovány pro spuštění aplikace. Například .exe nebo soubory aplikace s označením datových souborů musí patřit do **(povinné)** skupiny.  
  
 Výchozí stav publikování je označené hodnotou souboru **(automaticky)**. Například .exe aplikace je ve stavu publikovat **Include (Auto)** ve výchozím nastavení.  
  
 Soubory s **akce sestavení** vlastnost nastavena na hodnotu **obsahu** jsou označeny jako soubory aplikace a budou označeny jako zahrnuté ve výchozím nastavení. Můžete být zahrnuty, vyloučit nebo označeny jako datové soubory. Výjimky jsou následující:  
  
-   Datové soubory, jako je SQL databáze (MDF a MDB) a soubory XML se označí jako data souborů ve výchozím nastavení.  
  
-   Odkazy na sestavení (soubory .dll), jsou určené následujícím způsobem, když přidáte odkaz na: Pokud **Kopírovat místně** je **False**, je označena ve výchozím nastavení jako požadované sestavení (**požadovaných součástí ( Automaticky)**), který musí být k dispozici v mezipaměti GAC, předtím, než se aplikace nainstaluje. Pokud **Kopírovat místně** je **True**, je sestavení označeno ve výchozím nastavení jako sestavení aplikace (**Include (Auto)**) a budou zkopírovány do složky aplikace během instalace. Odkaz modelu COM se zobrazí v **soubory aplikace** dialogové okno pole (jako soubor .ocx) pouze v případě jeho **izolované** je nastavena na **True**. Ve výchozím nastavení bude součástí.  
  
### <a name="to-add-files-to-the-application-files-dialog-box"></a>Chcete-li přidat soubory do dialogového okna aplikace soubory  
  
1.  Vyberte soubor dat v **Průzkumníka řešení**.  
  
2.  V okně Vlastnosti změňte **akce sestavení** vlastnost **obsahu** hodnotu.  
  
### <a name="to-exclude-files-from-clickonce-publishing"></a>Vyloučení souborů z publikování ClickOnce  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **soubory aplikace** tlačítko Otevřít **soubory aplikace** dialogové okno.  
  
4.  V **soubory aplikace** dialogovém okně vyberte soubor, který chcete vyloučit.  
  
5.  V **stav publikování** pole, vyberte **vyloučit** z rozevíracího seznamu.  
  
### <a name="to-mark-files-as-data-files"></a>K označení souborů jako datových souborů  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **soubory aplikace** tlačítko Otevřít **soubory aplikace** dialogové okno.  
  
4.  V **soubory aplikace** dialogovém okně vyberte soubor, který chcete označit jako data.  
  
5.  V **stav publikování** pole, vyberte **datový soubor** z rozevíracího seznamu.  
  
### <a name="to-mark-files-as-prerequisites"></a>K označení souborů jako požadavky  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **soubory aplikace** tlačítko Otevřít **soubory aplikace** dialogové okno.  
  
4.  V **soubory aplikace** dialogového okna, vyberte sestavení aplikace (soubor .dll), kterou chcete označit jako předpoklad. Všimněte si, že vaše aplikace musí mít odkaz na sestavení aplikace v pořadí, aby se zobrazí v seznamu.  
  
5.  V **stav publikování** pole, vyberte **požadavků** z rozevíracího seznamu.  
  
### <a name="to-add-a-new-file-group"></a>Chcete-li přidat novou skupinu souborů  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **soubory aplikace** tlačítko Otevřít **soubory aplikace** dialogové okno.  
  
4.  V **soubory aplikace** dialogové okno, vyberte **skupiny** pole pro soubor, který chcete zahrnout do nové skupiny.  
  
    > [!NOTE]
    >  Soubory musí mít **akce sestavení** vlastnost nastavena na hodnotu **obsahu** před názvy souborů se zobrazí v **soubory aplikace** dialogové okno.  
  
5.  V **skupina pro stažení** pole, vyberte  **\<nový … >** z rozevíracího seznamu.  
  
6.  V **nová skupina** dialogové okno, zadejte název pro skupinu a potom klikněte na tlačítko **OK**.  
  
### <a name="to-add-a-file-to-a-group"></a>Přidání souboru do skupiny  
  
1.  S projekt vybraný v **Průzkumníka řešení**na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **publikovat** kartu.  
  
3.  Klikněte na tlačítko **soubory aplikace** tlačítko Otevřít **soubory aplikace** dialogové okno.  
  
4.  V **soubory aplikace** dialogové okno, vyberte **skupiny** pole pro soubor, který chcete zahrnout do nové skupiny.  
  
5.  V **skupina pro stažení** vyberte skupinu z rozevíracího seznamu.  
  
    > [!NOTE]
    >  Nelze změnit **skupina pro stažení** pro soubory, které jsou požadovány pro spuštění aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Publikování aplikací ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Postupy: Publikování aplikace ClickOnce pomocí průvodce publikováním](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)



