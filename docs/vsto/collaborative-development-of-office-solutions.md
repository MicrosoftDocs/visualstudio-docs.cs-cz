---
title: Spolupráce na vývoji řešení pro systém Office
description: Zjistěte, jak může více vývojářů pracovat na projektu Office stejným způsobem jako spolupráce na jiných projektech sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 028530014afdc78ab6c9c0483c3d443195383793
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942305"
---
# <a name="collaborative-development-of-office-solutions"></a>Spolupráce na vývoji řešení pro systém Office
  V projektu Office může pracovat s více vývojáři stejným způsobem jako spolupracovat na jiných projektech sady Visual Studio. Visual Studio správně vyhledá systém Microsoft Office instalaci na každém počítači, i když je Office nainstalovaný v různých umístěních. Je ale potřeba mít na paměti několik důležitých informací.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Vlastnosti ladění nejsou sdílené.
 Vlastnosti ladění nejsou sdíleny mezi více uživateli v rámci správy zdrojového kódu. Projekty Visual Basic a Visual C# ukládají vlastnosti ladění do souboru specifického pro uživatele (*ProjectName*. vbproj. User nebo *ProjectName*. csproj. User) a tento soubor není pod správou zdrojových kódů. Pokud je ladění více než jedna osoba, musí každá osoba zadat vlastnosti ladění ručně.

 Pokud je projekt umístěn ve sdílené síťové složce místo ve správě zdrojového kódu, je nutné provést některé další kroky, aby mohli vývojáři spolupracovat na otevření řešení a testování sestavení.

## <a name="source-control-requires-checking-out-all-files"></a>Správa zdrojového kódu vyžaduje rezervaci všech souborů.
 Použijete-li pro své projekty správu zdrojového kódu, měli byste rezervovat všechny soubory v souboru kódu v **Průzkumník řešení** (například soubory kódu *ThisDocument*, *ThisWorkbook* nebo *ThisAddIn* ) pokaždé, když změníte soubor s kódem, dokonce i soubory, které jsou ve výchozím nastavení skryté. Pokud se rezervuje jenom soubor s kódem nejvyšší úrovně, změny se můžou ztratit.

 Až provedete změny, zkontrolujte všechny soubory zpátky. Další informace o skrytých souborech kódu v projektech naleznete v tématu [projekty pro systém Office v prostředí Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Zabezpečení pro neoficiální spolupráci v síti
 Pro všechna řešení na úrovni dokumentu, která jsou v síťovém umístění (například \\ \\ *servername* \\ *název_sdílené_položky*), je nutné do seznamu důvěryhodných složek v aplikaci systém Microsoft Office, se kterou pracujete, přidat plně kvalifikované umístění. Vyberte možnost zahrnutí podadresářů do hlavní složky, nebo konkrétně přidejte složky pro ladění a sestavení do seznamu důvěryhodných složek. Další informace o tom, jak to provést, najdete v tématu [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

 Dočasné certifikáty, které jsou automaticky generovány při sestavování, nejsou zabezpečeny heslem. Certifikáty obsahují přihlašovací jméno vývojáře a další osobní údaje. Pokud nasadíte vlastní nastavení, která jsou podepsaná dočasnými certifikáty, můžou k těmto informacím mít přístup i ostatní.

## <a name="see-also"></a>Viz také
- [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)
- [Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)
- [Sestavování řešení pro systém Office](../vsto/building-office-solutions.md)
