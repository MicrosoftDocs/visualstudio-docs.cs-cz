---
title: Projekty a řešení – dialogové okno Možnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4230f99b78809594d65da991c65c11d7dc30efd4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246191"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Projekty a řešení – dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Nastaví výchozí cestu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] složky projektu a určí výchozí chování **výstup** okně **seznamu úkolů**, a **Průzkumníka řešení** jako projekty jsou vyvíjeny a sestaven. Chcete-li získat přístup k tomuto dialogovému oknu, klikněte na tlačítko **Nástroje / možnosti** rozbalte **projekty a řešení**a klikněte na tlačítko **Obecné**.  
  
> [!NOTE]
>  Dostupné možnosti v dialogových oknech, názvy a umístění příkazů, které vidíte, mohou lišit od informací uvedených v nápovědě v závislosti na aktivních nastaveních nebo edici. Tato stránka nápovědy byl zapsán s **obecného vývojového nastavení** v úvahu. Chcete-li zobrazit nebo změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="settings"></a>Nastavení  
 **Umístění projektů**  
 Nastaví výchozí umístění, kde jsou vytvářeny nové projekty a řešení složky a adresáře. Dialogová okna několika také použít tak umístění, nastavte tuto možnost pro složku počáteční body. Například dialogové okno Otevřít projekt používá toto umístění pro projekty zástupce.  
  
 **Umístění šablon projektů uživatele**  
 Nastaví výchozí umístění, která se používá **nový projekt** dialogové okno vytvořit seznam **šablony**. Další informace najdete v tématu [postupy: vyhledání a uspořádat šablony](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Umístění šablon položek uživatele**  
 Nastaví výchozí umístění, která se používá **přidat novou položku** dialogové okno vytvořit seznam **šablony**. Další informace najdete v tématu [postupy: vyhledání a uspořádat šablony](../../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
 **Vždy zobrazit seznam chyb-li sestavení dokončí s chybami**  
 Otevře **seznam chyb** okně při dokončení sestavení, pouze v případě, že projekt se nepovedlo sestavit. Se zobrazí chyby, ke kterým dochází během procesu sestavení. Když toto políčko zaškrtnuto, stále dochází k chybám, ale okno se neotevře, po dokončení sestavení. Tato možnost je povolená ve výchozím nastavení.  
  
 **Sledovat aktivní položku v Průzkumníku řešení**  
 Pokud je vybráno, **Průzkumníka řešení** automaticky otevře a aktivní položky je vybrána. Vybraná položka změny při práci s různé soubory v projektu nebo řešení nebo různé součásti v návrháři. Pokud tato možnost vybrána, výběr v **Průzkumníka řešení** nezmění automaticky. Tato možnost je povolená ve výchozím nastavení.  
  
 **Zobrazit pokročilou konfiguraci sestavení**  
 Při výběru možnosti konfigurace sestavení se zobrazí na **stránky vlastností projektu** dialogové okno a **stránek vlastností řešení** dialogové okno. Není-li zaškrtnuto, možnosti konfigurace sestavení nejsou zobrazeny na **stránky vlastností projektu** dialogové okno a **stránek vlastností řešení** dialogové okno pro [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] a [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projekty obsahující jednu konfiguraci nebo dvě konfigurace debug a release. Pokud projekt obsahuje konfigurace definovaná uživatelem, jsou uvedeny možnosti konfigurace sestavení.  
  
 Při zrušení výběru, příkazy na **sestavení** nabídky, jako například **sestavit řešení**, **znovu sestavit řešení**, a **Vyčistit řešení**, jsou proveden na konfiguraci vydané verze a příkazy na **ladění** nabídky, například **spustit ladění** a **spustit bez ladění**, jsou prováděny na konfiguraci ladění.  
  
 **Vždy zobrazit řešení**  
 Při výběru řešení a všechny příkazy, které fungují v řešení jsou vždy zobrazen v integrovaném vývojovém prostředí. Není-li zaškrtnuto, všechny projekty byly vytvořeny jako samostatné projekty a nevidíte řešení v Průzkumníku řešení nebo příkazy, které fungují v řešení v integrovaném vývojovém prostředí Pokud řešení obsahuje pouze jeden projekt.  
  
 **Uložit nové projekty při vytvoření**  
 Pokud je vybráno, můžete zadat umístění pro váš projekt v **nový projekt** dialogové okno. Není-li zaškrtnuto, všechny nové projekty jsou vytvořeny jako dočasné projekty. Při práci s dočasné projekty, můžete vytvořit a experimentovat s projektem, aniž byste museli zadat umístění na disku.  
  
 **Upozornit uživatele, pokud umístění projektu není důvěryhodné**  
 Při pokusu o vytvoření nového projektu nebo otevřete existující projekt do umístění, které není plně důvěryhodné (třeba na cestu UNC nebo cesta k protokolu HTTP), zobrazí se zpráva. Tuto možnost použijte k určení, zda zpráva se zobrazí pokaždé, když se při pokusu o vytvoření nebo otevření projektu do umístění, které není plně důvěryhodné.  
  
 **Zobrazit okno výstup při spuštění sestavení**  
 Automaticky zobrazí v okně výstupu v integrovaném vývojovém prostředí od počátku řešení sestavení. Další informace najdete v tématu [postupy: řízení výstupního okna](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Tato možnost je povolená ve výchozím nastavení.  
  
 **Vyzvat k symbolickému přejmenování při přejmenování souborů**  
 Pokud je vybráno, zobrazí pole zprávy s dotazem, zda je či není [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] by měl také přejmenování všech referencí v projektu na prvek kódu.  
  
## <a name="see-also"></a>Viz také  
 [Dialogové okno Možnosti, Projekty a řešení, Sestavit a spustit](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)



