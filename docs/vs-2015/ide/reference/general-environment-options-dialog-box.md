---
title: Obecné, prostředí, dialogové okno Možnosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83fc6adeba0529be03a9a982713d0584a2a7bc45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661265"
---
# <a name="general-environment-options-dialog-box"></a>Obecné, prostředí, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tato stránka slouží ke změně barevných motivů, nastavení stavového řádku a přidružení přípon souborů mezi další možnosti pro integrované vývojové prostředí (IDE). K dialogovému oknu **Možnosti** můžete přistupovat otevřením nabídky **nástroje** , výběrem **Možnosti**, otevřením složky **prostředí** a kliknutím na stránku **Obecné** . Pokud se tato stránka v seznamu nezobrazí, zaškrtněte políčko **Zobrazit všechna nastavení** v dialogovém okně **Možnosti** .

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, otevřete nabídku **nástroje** a pak zvolte **Nastavení importu a exportu**. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="visual-experience"></a>Vizuální prostředí
 **Barevný motiv** Vyberte barevný motiv **Blue**, **světlé** nebo **tmavé** pro IDE.

 Můžete nainstalovat další předdefinované motivy a vytvořit vlastní motivy tak, že si stáhnete a nainstalujete **Editor barevných motivů sady Visual Studio 2015** z [Visual Studio Marketplace](https://marketplace.visualstudio.com). Po instalaci tohoto nástroje se v seznamu barevný motiv zobrazí další barevné motivy.

 Použití velkých a malých písmen v nabídkách řádků nabídek je ve výchozím nastavení v aplikaci Visual Studio 2015 v **nadpisech velkých a malých písmen** . Zrušte tuto možnost, pokud chcete nastavit **všechna velká písmena**.

 **Automatické přizpůsobení vizuálního prostředí na základě výkonu klienta** Určuje, zda sada Visual Studio nastaví automatické nastavení pro vizuální prostředí nebo zda je nastavení explicitně nastaveno. Tato úprava může měnit zobrazení barev z přechodů na ploché barvy, nebo může omezit použití animací v nabídkách nebo v automaticky otevíraných oknech.

 **Povolit komplexní klientské prostředí** Umožňuje plné vizuální prostředí sady Visual Studio, včetně přechodů a animací. Tuto možnost zrušte, pokud používáte připojení ke vzdálené ploše nebo starší grafické adaptéry, protože tyto funkce mohou mít v těchto případech špatný výkon. Tato možnost je dostupná, jenom když zrušíte zaškrtnutí políčka **automaticky upravit vizuální prostředí na základě možnosti klienta** .

 **Použít hardwarovou akceleraci grafiky, pokud je k dispozici** Používá hardwarovou akceleraci grafiky, je-li k dispozici, nikoli při akceleraci softwaru.

## <a name="other"></a>Další
 **Položky zobrazené v nabídce okna** Přizpůsobuje počet oken, která se zobrazí v seznamu Windows v nabídce **okna** . Zadejte číslo od 1 do 24. Ve výchozím nastavení je počet 10.

 **Položky zobrazené v seznamu naposledy použitých položek** Přizpůsobuje počet naposledy použitých projektů a souborů, které se zobrazí v nabídce **soubor** . Zadejte číslo od 1 do 24. Ve výchozím nastavení je počet 10. Toto je snadný způsob, jak načíst nedávno použité projekty a soubory.

 **Zobrazit stavový řádek** Zobrazí stavový řádek. Stavový řádek je umístěný v dolní části okna IDE a zobrazí informace o průběhu probíhajících operací.

 **Tlačítko Zavřít ovlivní pouze aktivní okno nástrojů** Určuje, že když se klikne na tlačítko **Zavřít** , zavře se jenom okno nástroje, které má fokus, a ne všechna okna nástrojů v ukotvené sadě. Tato možnost je vybrána ve výchozím nastavení.

 **Tlačítko automaticky skrýt ovlivní pouze aktivní okno nástrojů** Určuje, že po kliknutí na tlačítko pro **automatické skrývání** bude automaticky skryto okno nástroje, které má fokus, a ne všechna okna nástrojů v ukotvené sadě. Ve výchozím nastavení není tato možnost vybrána.

 **Správa přidružení souborů** Zobrazí dialogové okno **nastavit přidružení programu systému Windows** , kde můžete zobrazit přípony souborů pro položky, které jsou obvykle asociovány se sadou Visual Studio, a aktuální výchozí program pro otevření každého typu souboru. Pokud chcete, aby aplikace Visual Studio měla výchozí aplikaci pro typy souborů, které ještě nejsou přidružené, zvolte příponu souboru a pak zvolte **Uložit**.

 Tato možnost může být užitečná, pokud máte na stejném počítači nainstalované dvě verze sady Visual Studio a později odinstalujete jednu z verzí. Po odinstalaci se již v Průzkumníkovi souborů nezobrazí ikony pro soubory sady Visual Studio. Kromě toho systém Windows již nerozpozná aplikaci Visual Studio jako výchozí aplikaci pro úpravu těchto souborů. Tato možnost obnoví tato přidružení.

## <a name="see-also"></a>Viz také
 [Dialogové okno Možnosti prostředí](../../ide/reference/environment-options-dialog-box.md) [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)
