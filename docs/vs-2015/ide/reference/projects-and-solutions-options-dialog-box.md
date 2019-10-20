---
title: Projekty a řešení, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 245b453a3020e79b924cb8058ff392bd59673402
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662124"
---
# <a name="projects-and-solutions-options-dialog-box"></a>Projekty a řešení – dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nastaví výchozí cestu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] složek projektu a určí výchozí chování okna **výstup** , **seznam úkolů**a **Průzkumník řešeníy** při vývoji a sestavení projektů. Chcete-li získat přístup k tomuto dialogovému oknu, klikněte na tlačítko **Nástroje/možnosti** rozbalit **projekty a řešení**a klikněte na možnost **Obecné**.

> [!NOTE]
> Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídky, které vidíte, se mohou lišit od toho, co je popsáno v nápovědě v závislosti na aktivních nastaveních nebo edici. Tato stránka Help se napsala s ohledem na **Obecné nastavení vývoje** . Chcete-li zobrazit nebo změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Nastavení
 **Umístění projektů** Nastaví výchozí umístění, kde jsou vytvořeny nové projekty a složky řešení a adresáře. Několik dialogových oken používá pro výchozí body složky také umístění nastavené v této možnosti. Například dialogové okno otevřít projekt používá toto umístění pro zástupce moje projekty.

 **Umístění uživatelských šablon projektu** Nastaví výchozí umístění, které je používáno v dialogovém okně **Nový projekt** k vytvoření seznamu **mých šablon**. Další informace najdete v tématu [Postupy: hledání a organizace šablon](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Umístění šablon uživatelských položek** Nastaví výchozí umístění, které je používáno v dialogovém okně **Přidat novou položku** k vytvoření seznamu **mých šablon**. Další informace najdete v tématu [Postupy: hledání a organizace šablon](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

 **Při dokončení buildu vždycky zobrazit seznam chyb s chybami** Otevře okno **Seznam chyb** při dokončování sestavení, pouze pokud se projekt nepovedlo sestavit. Zobrazí se chyby, ke kterým dojde během procesu sestavení. Pokud je tato možnost smazána, k chybám stále dochází, ale okno není po dokončení sestavení otevřeno. Tato možnost je ve výchozím nastavení povolená.

 **Sledovat aktivní položku v Průzkumník řešení** Když se tato možnost vybere, **Průzkumník řešení** se automaticky otevře a vybere se aktivní položka. Vybraná položka se mění při práci s různými soubory v projektu nebo řešení nebo v různých součástech v návrháři. Pokud je tato možnost vymazána, výběr v **Průzkumník řešení** se nemění automaticky. Tato možnost je ve výchozím nastavení povolená.

 **Zobrazit pokročilé konfigurace sestavení** Je-li vybrána tato možnost, možnosti konfigurace sestavení se zobrazí v dialogovém okně **stránky vlastností projektu** a v dialogovém okně **stránky vlastností řešení** . Pokud je zaškrtnuto, možnosti konfigurace sestavení se nezobrazují v dialogovém okně **stránky vlastností projektu** a v dialogovém okně **stránky vlastností řešení** pro [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] a [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projekty, které obsahují jednu konfiguraci, nebo tyto dvě konfigurace ladění a vydaná verze. Pokud má projekt uživatelsky definované konfigurace, zobrazí se možnosti konfigurace sestavení.

 Pokud není vybráno, příkazy v nabídce **sestavení** , jako je **sestavení řešení**, **opětovné sestavení řešení**a **Vyčištění**, jsou prováděny v konfiguraci vydané verze a příkazy v nabídce **ladění** , jako je například **Start. Ladění** a **spouštění bez ladění**se provádí v konfiguraci ladění.

 **Vždy zobrazit řešení** Je-li toto políčko zaškrtnuto, řešení a všechny příkazy, které fungují na řešení, jsou vždy zobrazeny v integrovaném vývojovém prostředí. Pokud je zaškrtnuto, všechny projekty jsou vytvořeny jako samostatné projekty a toto řešení se nezobrazuje v Průzkumník řešení nebo příkazy, které fungují na řešeních v rozhraní IDE, pokud řešení obsahuje pouze jeden projekt.

 **Uložit nové projekty při vytvoření** Když je tato možnost vybrána, můžete v dialogovém okně **Nový projekt** zadat umístění pro projekt. Po zaškrtnutí budou všechny nové projekty vytvořeny jako dočasné projekty. Při práci s dočasnými projekty můžete vytvořit a experimentovat s projektem bez nutnosti zadávat umístění na disku.

 **Upozornit uživatele, pokud umístění projektu není důvěryhodné** Pokud se pokusíte vytvořit nový projekt nebo otevřít existující projekt v umístění, které není plně důvěryhodné (například na cestě UNC nebo v cestě HTTP), zobrazí se zpráva. Tuto možnost použijte, chcete-li určit, zda se zpráva zobrazí při každém pokusu o vytvoření nebo otevření projektu v umístění, které není plně důvěryhodné.

 **Zobrazit okno výstup při zahájení sestavování** Automaticky zobrazuje okno Výstup v rozhraní IDE na začátku sestavení řešení. Další informace naleznete v tématu [How to: Control a okno výstup](https://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858). Tato možnost je ve výchozím nastavení povolená.

 **Při přejmenování souborů zobrazit výzvu k zadání symbolického názvu** Je-li vybrána tato možnost, zobrazí okno se zprávou s dotazem, zda [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] má také přejmenovat všechny odkazy v projektu na prvek kódu.

## <a name="see-also"></a>Viz také
 [Dialogové okno Možnosti, Projekty a řešení, Sestavit a spustit](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
