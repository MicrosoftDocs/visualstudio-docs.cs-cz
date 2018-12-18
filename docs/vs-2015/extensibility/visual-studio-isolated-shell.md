---
title: Izolované prostředí sady Visual Studio | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d7fcb0a838f2849ab74d202785709164ec5af6d7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740658"
---
# <a name="visual-studio-isolated-shell"></a>Izolované prostředí sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio izolované prostředí umožňuje vytvářet samostatné aplikace, které lze spustit vedle sebe s jinými verzemi nástroje Visual Studio. Se používá především k hostování specializované nástroje, které můžete používat služby Visual Studio, ale také mít přizpůsobený vzhled a značky. Funkce sady Visual Studio a pro skupinu příkazů nabídky je možné snadno zapnout a vypnout. Názvy aplikací, ikony aplikace a úvodní obrazovky jsou plně přizpůsobitelné. Seznam přizpůsobitelných funkcí najdete v tématu [přizpůsobení izolovaného prostředí](../extensibility/customizing-the-isolated-shell.md).  
  
 Pro práci s projektem izolovaného prostředí, je nutné nainstalovat sadu Visual Studio SDK. Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 K vytvoření aplikací izolovaného prostředí, začněte s projektem Visual Studio Shell izolované. Tento projekt obsahuje všechno, co potřebujete k vývoji a testování aplikace izolované prostředí. Až budete připravení k zápisu instalační program, který nasadí vaši aplikaci, musíte získat Distribuovatelný balíček prostředí isolated shell z [Distribuovatelný balíček prostředí Microsoft Visual Studio Shell (izolovaný režim)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Před přístupem k Distribuovatelný balíček prostředí isolated shell, budete požádáni o vyplnění stručného zákaznického dotazníku.  Po vyplnění, budete přesměrováni na stránku Visual Studio Connect s odkazy na stažení balíčku k opětovné distribuci.  Odkazy ke stažení najdete na následné návštěvy webu Visual Studio Connect pod **programy &#124; VISUAL STUDIO 2015 integrované a IZOLOVANÉHO prostředí** kartu.  
  
> [!NOTE]
>  Další informace o tom, jak nasadit aplikaci izolovaného prostředí, najdete v části [návod: vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Práce s izolovaného prostředí  
 Aplikace Visual Studio izolované prostředí má úplný přístup ke službám Visual Studio a podporuje speciální přizpůsobení a značky. Existuje několik způsobů, jak můžete přizpůsobit aplikací izolovaného prostředí:  
  
- Součástí rozšíření VSPackages a Managed Extensibility Framework (MEF) můžete použít k rozšíření aplikací izolovaného prostředí, stejně jako můžete využít v jakékoli jiné rozšíření sady Visual Studio. Další informace najdete v tématu [rozšíření izolovaného prostředí](../extensibility/extending-the-isolated-shell.md).  
  
- Chcete-li funkce aplikace Visual Studio a pro skupinu příkazů nabídky k dispozici nebo není k dispozici, aktualizujte soubor .vsct v projektu uživatelské rozhraní (UI) aplikace.  
  
- Chcete-li odebrat **možnosti** stránky ani jiné součásti sady Visual Studio shell z aplikace, aktualizace souboru .pkgundef aplikace.  
  
- Pokud chcete upravit další aspekty vzhledu a chování prostředí, aktualizujte soubor .pkgdef aplikace.  
  
- Některé aspekty prostředí je taky možné specifikovat při spuštění aplikace. Provedete to tak, aktualizujte parametry v volání Start vstupní bod appenvstub.dll.  
  
  Další informace o různých prvků, které můžete přizpůsobit, najdete v části [prvky izolovaného prostředí](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standardní funkce izolovaného prostředí  
 Následující funkce jsou standardní pro všechny edice sady Visual Studio.  
  
|Kategorie funkce|Funkce|  
|----------------------|-------------|  
|Funkce integrovaného vývojového prostředí|Import a Export nastavení<br /><br /> Instalační program ovládací prvek panelu nástrojů<br /><br /> Seznam úkolů a seznam chyb<br /><br /> Okno Výstup<br /><br /> Úvodní stránka<br /><br /> Okno vlastností<br /><br /> Sada nástrojů<br /><br /> Průzkumník řešení<br /><br /> Okno záložek<br /><br /> zobrazení tříd<br /><br /> prohlížeč objektů<br /><br /> Příkazové okno<br /><br /> Osnova dokumentu<br /><br /> Zobrazení prostředků<br /><br /> Externí nástroje<br /><br /> Přidání odkazu na službu Windows Communication Foundation (WCF)<br /><br /> Language Integrated Query (LINQ) podpory|  
|Editoru nebo návrháře|Procházení nástroje (jednotné hledání, definici zdroje, dědičnost) kódu<br /><br /> IntelliSense<br /><br /> Inteligentní značky<br /><br /> Správce fragmentů kódů<br /><br /> Fragmenty kódu<br /><br /> Refaktoring<br /><br /> Přehlednou výpis<br /><br /> Filtrování IntelliSense<br /><br /> Definice kódu – okno<br /><br /> Návrhář aplikace<br /><br /> Návrhář formulářů Windows<br /><br /> Návrhář Windows Presentation Foundation (WPF)|  
|Ladění|Vyhodnocovač výrazů jazyka C#<br /><br /> Místní ladění<br /><br /> Spravované ladění<br /><br /> Upravit a pokračovat<br /><br /> Ladění mezi vlákny<br /><br /> vizualizace<br /><br /> DataTips<br /><br /> Nativní ladění<br /><br /> Ladění skriptů<br /><br /> Definiční ladění<br /><br /> Ladění just-in-time (JIT)<br /><br /> Ladění více procesů<br /><br /> Ladění XSLT<br /><br /> Připojit k místní procesu<br /><br /> Body trasování<br /><br /> Omezení zarážku|  
|Data|Průzkumník serveru (zjednodušené - jenom Data)<br /><br /> Datové připojení k místním datům (. MDF nebo. MDB)<br /><br /> Vazba dat na objektu<br /><br /> Datové vazby k webové službě<br /><br /> Úplnou sadu ovládací prvky dat<br /><br /> XML editor<br /><br /> Datové připojení k místní databázi serveru<br /><br /> okno Zdroje dat|  
|Web|Editor HTML<br /><br /> Webový prohlížeč<br /><br /> Návrhář webových formulářů<br /><br /> Webový projekt<br /><br /> Projekt webové aplikace|  
|Rozšiřitelnost|Využívá komponenty rozšíření VSPackages a rozhraní MEF|  
  
## <a name="see-also"></a>Viz také  
 [Prostředí (izolované nebo integrované)](../extensibility/shell-isolated-or-integrated.md)

