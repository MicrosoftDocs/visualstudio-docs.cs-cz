---
title: Izolované prostředí sady Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef2d1cbffab5e38e603b0e50beb896f1c6efa23d
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919206"
---
# <a name="visual-studio-isolated-shell"></a>Izolované prostředí sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Izolované prostředí nástroje Visual Studio umožňuje vytvářet samostatné aplikace, které mohou běžet souběžně s jinými verzemi nástroje Visual Studio. Používá se primárně pro hostování specializovaných nástrojů, které mohou používat služby sady Visual Studio, ale také vlastní vzhled a branding. Funkce sady Visual Studio a skupiny příkazů nabídky lze snadno zapnout nebo vypnout. Názvy aplikací, ikony aplikací a úvodní obrazovky jsou plně přizpůsobitelné. Seznam přizpůsobitelných funkcí najdete v tématu [přizpůsobení izolovaného prostředí](../extensibility/customizing-the-isolated-shell.md).  
  
 Chcete-li pracovat s projektem izolovaného prostředí, je nutné nainstalovat sadu Visual Studio SDK. Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Chcete-li vytvořit aplikaci izolovaného prostředí, začněte s projektem s izolovaným prostředím sady Visual Studio. Tento projekt obsahuje vše, co potřebujete k vývoji a testování vlastní aplikace izolovaného prostředí. Až budete připraveni k napsání instalačního programu, který nasadí vaši aplikaci, musíte získat Distribuovatelný balíček izolovaného prostředí z [prostředí sady Microsoft Visual Studio (izolovaný režim) Distribuovatelný balíček](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).  
  
> [!NOTE]
> Předtím, než budete moci získat přístup k distribuovatelnýmu balíčku izolovaného prostředí, budete požádáni o vyplnění stručného průzkumu zákazníka.  Po jeho vyplnění budete přesměrováni na stránku Visual Studio Connect s odkazy pro stažení distribuovatelných balíčků.  Odkazy ke stažení najdete v následujících návštěvách na webu Visual Studio Connect na kartě programy v **integrovaném a izolovaném prostředí sady &#124; Visual Studio 2015** .  
  
> [!NOTE]
> Další informace o tom, jak nasadit izolovanou aplikaci založenou na prostředí, najdete v tématu [Návod: Vytvoření základní aplikace izolovaného prostředí](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Práce s izolovaným prostředím  
 Aplikace izolovaného prostředí sady Visual Studio má plný přístup ke službám sady Visual Studio a podporuje speciální přizpůsobení a branding. Existuje několik způsobů, jak můžete přizpůsobit aplikaci izolovaného prostředí:  
  
- Můžete použít součásti VSPackage a Managed Extensibility Framework (MEF) k rozšíření aplikace izolovaného prostředí stejným způsobem, jako byste je používali v jakémkoli jiném rozšíření sady Visual Studio. Další informace najdete v tématu [rozšíření izolovaného prostředí](../extensibility/extending-the-isolated-shell.md).  
  
- Chcete-li zpřístupnit nebo nedostupné skupiny příkazů sady Visual Studio, aktualizujte soubor. vsct v projektu uživatelského rozhraní (UI) aplikace.  
  
- Chcete-li odebrat stránky **možností** nebo jiné součásti prostředí sady Visual Studio z aplikace, aktualizujte soubor. pkgundef aplikace.  
  
- Chcete-li upravit jiné aspekty vzhledu nebo chování prostředí, aktualizujte soubor. pkgdef aplikace.  
  
- Některé aspekty prostředí lze také zadat při spuštění aplikace. Provedete to tak, že aktualizujete parametry ve volání počátečního vstupního bodu knihovny Appenvstub. dll.  
  
  Další informace o různých prvcích, které lze přizpůsobit, naleznete v tématu [prvky izolovaného prostředí](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Standardní funkce izolovaného prostředí  
 Následující funkce jsou standardní pro všechny edice sady Visual Studio.  
  
|Kategorie funkce|Funkce|  
|----------------------|-------------|  
|Funkce IDE|Nastavení importu a exportu<br /><br /> Instalační program ovládacího prvku sady nástrojů<br /><br /> Seznam úkolů & Seznam chyb<br /><br /> Okno Výstup<br /><br /> Domovská stránka<br /><br /> Okno vlastností<br /><br /> Sada nástrojů<br /><br /> Průzkumník řešení<br /><br /> Okno záložek<br /><br /> zobrazení tříd<br /><br /> Prohlížeč objektů<br /><br /> Okno Příkaz<br /><br /> Osnova dokumentu<br /><br /> Prostředky<br /><br /> Externí nástroj<br /><br /> Windows Communication Foundation (WCF) Přidat odkaz na službu<br /><br /> Podpora jazyka LINQ (Language Integrated Query)|  
|Editor/Návrhář|Nástroje pro procházení kódu (sjednocené hledání, definice zdroje, dědičnost)<br /><br /> IntelliSense<br /><br /> SmartTags<br /><br /> Správce fragmentů kódu<br /><br /> Fragmenty kódu<br /><br /> Refaktoring<br /><br /> Poměrně se seznamem<br /><br /> Filtrování IntelliSense<br /><br /> Okno definice kódu<br /><br /> Návrhář aplikace<br /><br /> Návrhář formulářů Windows<br /><br /> Návrhář Windows Presentation Foundation (WPF)|  
|Ladění|C#Vyhodnocení výrazu<br /><br /> Místní ladění<br /><br /> Spravované ladění<br /><br /> Upravit a pokračovat<br /><br /> Ladění mezi vlákny<br /><br /> Vizualizace<br /><br /> DataTips<br /><br /> Nativní ladění<br /><br /> Ladění skriptů<br /><br /> Ladění spolupráce<br /><br /> Ladění JIT (just-in-time)<br /><br /> Ladění více procesů<br /><br /> Ladění XSLT<br /><br /> Připojit k místnímu procesu<br /><br /> Body trasování<br /><br /> Omezení zarážek|  
|Datové|Průzkumník serveru (jenom zjednodušená data)<br /><br /> Vazba dat na místní data (. MDF nebo. DATABÁZI<br /><br /> Vázání dat na objekt<br /><br /> Vázání dat na webovou službu<br /><br /> Úplná sada ovládacích prvků dat<br /><br /> Editor XML<br /><br /> Vazba dat na místní databázový server<br /><br /> okno Zdroje dat|  
|Web|Editor HTML<br /><br /> Webový prohlížeč<br /><br /> Návrhář webových formulářů<br /><br /> Projekt webu<br /><br /> Projekt webové aplikace|  
|Rozšiřitelnost|Spotřebovává VSPackage a komponenty MEF.|  
  
## <a name="see-also"></a>Viz také  
 [Prostředí (izolované nebo integrované)](../extensibility/shell-isolated-or-integrated.md)
