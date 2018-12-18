---
title: Přesouvání rozšíření Visual Studia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c646ec2c5159e6c3551776761baa9328e3d62bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142750"
---
# <a name="shipping-visual-studio-extensions"></a>Přesouvání rozšíření Visual Studia
Po dokončení vývoje rozšíření, nainstalujte ji na jiné počítače, sdílet se svými přáteli a spolupracovníky nebo ji zveřejnit na Visual Studio Marketplace. V této části vám vysvětlíme, vše, co musíte udělat, aby bylo možné publikovat a spravovat rozšíření: práce se soubory VSIX, publikování, lokalizace a aktualizace.  
  
## <a name="working-with-vsix-extensions"></a>Práce s příponami VSIX  
 Vytváření prázdného projektu VSIX a následným přidáním šablon položek s jiný k ní můžete vytvořit VSIX rozšíření. Další informace najdete v tématu [šablona projektu VSIX](../extensibility/vsix-project-template.md).  
  
 Formát VSIX můžete použít k balíčku šablony projektů, položku součásti šablony, VSPackages, Managed Extensibility Framework (MEF), **sada nástrojů** ovládací prvky, sestavení a vlastní typy (to zahrnuje vlastní stránky Start). Formát VSIX využívá nasazení založené na souboru. Další informace o balíčcích VSIX najdete v tématu [anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).  
  
 Formát VSIX nepodporuje instalaci fragmenty kódu. Některé další scénáře, jako je zápis do globální mezipaměti sestavení (GAC) nebo do registru systému také nejsou podporovány. Pokud potřebujete k zápisu do mezipaměti GAC nebo registru v instalaci, musíte použít instalační služby systému Windows. Další informace najdete v tématu [Příprava rozšíření pro nasazení systému Windows instalační program](../extensibility/preparing-extensions-for-windows-installer-deployment.md).  
  
## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publikování rozšíření v sadě Visual Studio Marketplace  
 Rozšíření jiným lidem můžete distribuovat jednoduše tak, že je souboru VSIX poštovní nebo uvedení v na serveru. Ale nejlepší způsob, jak získat kódu do nesprávných rukou velký počet uživatelů se umístí jej [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Visual Studio Marketplace rozšíření jsou k dispozici uživatelům v sadě Visual Studio prostřednictvím **rozšíření a aktualizace**. Další informace najdete v tématu [hledání a používání rozšíření Visual Studia](../ide/finding-and-using-visual-studio-extensions.md).  
  
 Úplný příklad, který ukazuje, jak nahrát rozšíření pro Visual Studio Marketplace najdete v tématu [návod: publikování rozšíření Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).  
  
## <a name="private-galleries"></a>Privátní Galerie  
 Když budete vyvíjet ovládací prvky, šablony a nástroje, můžete je sdílet ve vaší organizaci je zveřejněním privátní Galerie na vašem intranetu. Další informace najdete v tématu [privátní Galerie](../extensibility/private-galleries.md).  
  
## <a name="localizing-your-extension"></a>Lokalizace rozšíření  
 Pokud se chystáte verzi rozšíření v různá národní prostředí, měli byste zvážit lokalizace ho. Vysvětlení, co je zahrnuta, najdete v článku [lokalizace balíčky VSIX](../extensibility/localizing-vsix-packages.md).  
  
## <a name="updating-and-versioning-your-extension"></a>Aktualizace a správa verzí rozšíření  
 Po publikování rozšíření, vrátí se po dobu, pokud je potřeba aktualizovat. Postup aktualizace rozšíření, které se publikoval na Visual Studio Marketplace naleznete v tématu [postup: aktualizace rozšíření](../extensibility/how-to-update-a-visual-studio-extension.md).  
  
 Můžete nastavit rozšíření pro podporu více verzí sady Visual Studio. Další informace najdete v tématu [podpora více verzí aplikace Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Začínáme se šablonou projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Vysvětluje, jak nainstalovat vlastní šablonu projektu pomocí šablony projektu VSIX.|  
|[Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Popisuje součásti balíčku VSIX.|  
|[Šablona projektu VSIX](../extensibility/vsix-project-template.md)|Poskytuje podrobné pokyny o tom, jak balíčku a publikování rozšíření.|  
|[Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md)|Vysvětluje, jak zajistit textu pro proces instalace pomocí souborů extension.vsixlangpack.|  
|[Postupy: aktualizace rozšíření](../extensibility/how-to-update-a-visual-studio-extension.md)|Popisuje postup aktualizace rozšíření ve vašem systému a jak nasadit aktualizace do stávající rozšíření sady Visual Studio.|  
|[Postupy: Přidání závislosti k balíčku VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Popisuje postup přidání odkazy na balíčky pro nasazení VSIX.|  
|[Příprava rozšíření pro nasazení Instalační služby systému Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Vysvětluje, jak nasadit rozšíření pomocí Instalační služby systému Windows.|  
|[Podepisování balíčků VSIX](../extensibility/signing-vsix-packages.md)|Vysvětluje, jak k podepisování balíčků VSIX.|  
|[Privátní galerie](../extensibility/private-galleries.md)|Vysvětluje, jak vytvářet privátní Galerie pro rozšíření.|  
|[Podpora více verzí sady Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Ukazuje, jak získat podporu rozšíření více verzí sady Visual Studio.|
|[Vyhledání sady Visual Studio](locating-visual-studio.md)|Popisuje, jak najít instance Visual Studio pro nasazení vlastního rozšíření.|
