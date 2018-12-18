---
title: Vytváření balíčku Instalační služby systému Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edb0a1d385129600372fc26693aec729751a768c
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512865"
---
# <a name="author-a-windows-installer-package"></a>Autor balíčku Instalační služby systému Windows
Datové jednotky modelu Instalační služby systému Windows. Místo psaní skriptu procedury kopírování souborů a zápis položky registru, například vytváříte řádků a sloupců do tabulek databáze, které obsahují data souborů a registru.  
  
## <a name="database-entries"></a>Položky databáze  
K instalaci VSPackage balíček Instalační služby systému Windows musí obsahovat položky databáze k provádění následujících úloh:  
  
- Hledat systému k vyhledání verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podporuje vašeho balíčku VSPackage (pomocí tabulek Instalační služby systému Windows, které zahrnují AppSearch CompLocator, RegLocator, DrLocator a podpis).  
  
- Zrušit instalaci, pokud žádné podporovanou verzi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je nainstalovaná, nebo pokud jiné požadavky na systém ze sady VSPackage není splněná (pomocí tabulky LaunchCondition).  
  
- Instalace balíčku VSPackage a závislé soubory (pomocí adresáře, komponenty a soubor tabulky).  
  
- Přidejte do registru (pomocí tabulky registru) odpovídajícími informacemi pro sady VSPackage.  
  
- Integrace sady VSPackage v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] voláním **/Setup devenv.exe** (pomocí tabulky CustomAction).  
  
Další informace najdete v tématu [Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-portal).
  
## <a name="setup-tools"></a>Instalační program nástroje  
Různé nástroje třetích stran instalace nabízejí vývojové prostředí pro balíčky Instalační služby systému Windows. Tyto bezplatné nástroje vám budou k dispozici:  
  
- Program InstallShield limited edition  
  
   Pomocí sady Visual Studio můžete získat omezenou verzi InstallShield **nový projekt** dialogového okna. Rozbalte **ostatní typy projektů** a pak vyberte **instalace a nasazení**. Vyberte šablonu InstallShield.  
  
- Sada nástrojů XML Instalační služby systému Windows  
  
   Sada nástrojů XML Instalační služby systému Windows (WiX) sestaví balíčky Instalační služby systému Windows ze zdrojových souborů XML. Sada nástrojů WiX je projekt open source Microsoftu. Stáhněte si zdrojový kód a spustitelné soubory z [sadu nástrojů Wix toolset](http://sourceforge.net/projects/wix).  
  
   Pro komerční produkty, které se integrují do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pomocí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], naleznete v tématu [ http://visualstudiogallery.com ](http://visualstudiogallery.com/).  
  
## <a name="see-also"></a>Viz také:  
 [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)