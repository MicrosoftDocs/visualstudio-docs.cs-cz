---
title: Vytváření balíčku Instalační služba systému Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58529dabbb52ceb751c67be24beb1d21285a1de6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301128"
---
# <a name="authoring-a-windows-installer-package"></a>Vytvoření balíčku Instalační služby systému Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Datové jednotky Instalační služba systému Windows modelu. Místo psaní skriptu procedurálního kopírování souborů a zápis položek registru například můžete vytvářet řádky a sloupce v databázových tabulkách, které obsahují data souborů a registru.  
  
## <a name="database-entries"></a>Databázové položky  
 Chcete-li nainstalovat VSPackage, balíček Instalační služba systému Windows musí obsahovat databázové položky, aby bylo možné provádět následující úlohy:  
  
- Vyhledejte v systému, kde najdete verze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] vaší sady VSPackage (pomocí Instalační služba systému Windows tabulek, které zahrnují AppSearch, CompLocator, RegLocator, DrLocator a Signature).  
  
- Zrušíte instalaci, pokud není nainstalovaná žádná podporovaná verze nástroje [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nebo pokud není splněn jiný požadavek na systém pro VSPackage (pomocí tabulky LaunchCondition).  
  
- Nainstalujte rozhraní VSPackage a závislé soubory (pomocí adresáře, komponenty a tabulek souborů).  
  
- Přidejte do registru vhodné informace pro VSPackage (pomocí tabulky registru).  
  
- Integrujte VSPackage do v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] voláním **devenv.exe/Setup** (pomocí tabulky CustomAction).  
  
  Další informace najdete v tématu [Instalační služba systému Windows](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx).  
  
## <a name="setup-tools"></a>Nástroje pro instalaci  
 Nejrůznější nástroje pro instalaci třetích stran poskytují vývojové prostředí pro Instalační služba systému Windows balíčky. Následující dva bezplatné nástroje:  
  
- InstallShield Limited Edition  
  
   Pomocí dialogového okna **Nový projekt** sady Visual Studio můžete získat omezené verze programu InstallShield. Rozbalte **jiné typy projektů** a potom vyberte **nastavení a nasazení**. Vyberte šablonu InstallShield.  
  
- Sada nástrojů XML pro Instalační službu systému Windows  
  
   Sada nástrojů vytváří Instalační služba systému Windows balíčky ze zdrojových souborů XML. Sada nástrojů je projekt Microsoft Open-Source. Zdrojový kód a spustitelné soubory si můžete stáhnout z [http://sourceforge.net/projects/wix](https://sourceforge.net/projects/wix/) .  
  
  Pro komerční produkty, které jsou integrovány do pomocí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] , viz [https://marketplace.visualstudio.com/](https://marketplace.visualstudio.com/) .  
  
## <a name="see-also"></a>Viz také  
 [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
