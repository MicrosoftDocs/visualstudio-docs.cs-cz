---
title: Prostředí sady Visual Studio (integrovaný režim) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f6e88e5c430129faa80f34a45f9b6620d5b0d13
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850363"
---
# <a name="visual-studio-shell-integrated"></a>Prostředí sady Visual Studio Shell (integrované)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Integrované prostředí nástroje Visual Studio zahrnuje integrované vývojové prostředí (IDE), ladicí program a integraci správy zdrojového kódu. Není zahrnutý žádný programovací jazyk. Integrované prostředí však poskytuje rozhraní, které umožňuje přidat programovací jazyky.  
  
 Integrované prostředí sady Visual Studio je ve skutečnosti kombinací izolovaného prostředí sady Visual Studio a další instalace, která zahrnuje integrované specifické součásti prostředí.  Integrovaná aplikace prostředí by měla obsahovat Distribuovatelný balíček prostředí pro distribuci z [prostředí sady Microsoft Visual Studio (izolovaný režim) Distribuovatelný balíček](https://docs.microsoft.com/collaborate/connect-redirect?ProgramID=8963&InvitationID=VS15-2R69-RB8J) i integrovaný Distribuovatelný balíček prostředí z [prostředí sady Microsoft Visual Studio (integrovaný režim) Distribuovatelný balíček](https://docs.microsoft.com/collaborate/connect-redirect?ProgramID=8963&InvitationID=VS15-2R69-RB8J).  
  
> [!NOTE]
> Než získáte přístup k distribuovatelným balíčkům izolovaného a integrovaného prostředí, budete požádáni o vyplnění stručného zákaznického dotazníku.  Po jeho vyplnění budete přesměrováni na stránku Visual Studio Connect s odkazy pro stažení distribuovatelných balíčků.  Odkazy ke stažení najdete v následujících návštěvách na webu Visual Studio Connect na kartě programy v **integrovaném a izolovaném prostředí sady &#124; Visual Studio 2015** .  
  
 Pokud nainstalujete integrovanou aplikaci prostředí do stejného počítače jako plnou verzi sady Visual Studio, komponenty vaší aplikace budou integrovány přímo do sady Visual Studio.  
  
## <a name="features-in-the-integrated-shell"></a>Funkce integrovaného prostředí  
  
|||  
|-|-|  
|Oblast funkcí|Funkce|  
|Podpora jazyků|-None|  
|IDE – integrované vývojové prostředí|<ul><li>Nastavení<br /><br /> <ul><li>Vytvořit nastavení</li><li>Nastavení importu a exportu</li><li>Resetovat nastavení</li></ul></li><li>Integrace **nástrojů**</li><li>Integrace **seznam úkolů**</li><li>Integrace s usnadněním</li><li>Dialogové okno **Možnosti**</li><li>Správa písem a barev</li><li>Okno **výstup**</li><li>**Příkazové** okno</li><li>Správa oken</li><li>Příkazy, nabídky a klíčové vazby</li><li>Modul runtime DSL (Domain-Specific Language)</li></ul>|  
|Systém projektů a typy projektů|– Řešení a složky řešení<br />– Řešení Configuration Manager<br />– Správa položek<br />– Single-Project a multi-project řešení<br />-Návrhář aplikací (zjednodušené vlastnosti projektu)<br />-Přidat webový odkaz<br />-Přidat odkaz na službu<br />– Jeden projekt<br />– Typy projektů webu<br />– Projekty webové aplikace|  
|Sestavit|– Vlastní kroky sestavení v integrovaném vývojovém prostředí<br />– Předběžná kompilace pro ochranu duševního vlastnictví (IP)<br />-Podepisování kódu<br />     MSBuild|  
|Editor|– Nástroje pro procházení kódu (sjednocené hledání, definice zdroje, dědičnost)<br />– Navigace v kódu<br />– IntelliSense<br />– Inteligentní značky<br />– Refaktoring<br />– Seznam s hodně<br />– Filtrování IntelliSense<br />-   okno **definice kódu**|  
|Návrhář|– Návrhář Windows Presentation Foundation<br />-Návrhář formulářů<br />– Návrhář webu a editor HTML|  
|Datové|-   **Průzkumník serveru** (zjednodušené: pouze data). Viz Poznámka 1.<br />-   okno **zdroje dat**<br />-Úplná sada ovládacích prvků dat<br />– Editor XML<br />-Vazba dat na místní zdroj dat (. MDF nebo. DATABÁZI<br />-Vazba dat na objekt<br />-Data BIND k webové službě<br />-Vazba dat na místní databázový server<br />-Vazba dat na vzdálený databázový server<br />– Nástroje DDL pro vzdálená data<br />Rozšiřitelnost -   **Průzkumník serveru** (ukázky[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)])|  
|Ladicí program|– Místní ladění. Viz poznámku 2.<br />– Spravované ladění<br />– Místní ladění<br />– Připojit k místnímu procesu<br />-Připojit ke vzdálenému procesu<br />– Anonymní delegát<br />– Aplikační domény<br />– Ladění ASPX<br />– Atributy<br />– Přerušení během vyhodnocení funkce<br />– Zarážky<br />-Omezení zarážek<br />– Zásobník volání<br />**příkazové** okno -   <br />– Ladění mezi vlákny<br />– Tipy pro data<br />– Vizualizér dat<br />– Podpora ladicího programu pro pomocníka spravovaného ladění (MDA)<br />-Podpora ladicího programu pro přeposílání typů<br />– Podpora DTEEvents spouští pro OTB<br />– JMC stepper<br />-Test AppID pro ladění (DBGCLR)<br />– Profil ladicího programu<br />– Nástroje a možnosti ladicího programu<br />-Iterátor ladění<br />-Vyhodnocení výrazu pro dobu návrhu<br />– C# Vyhodnocovací filtr výrazů<br />-Zpětný překlad<br />-Upravit a pokračovat<br />– Okna vyhodnocovacího filtru výrazů (kukátko, místní hodnoty, automatické hodnoty)<br />– Pomocník výjimek<br />– Výjimky<br />-Provedení<br />– Obecné typy<br />– Získání správného zdroje<br />– HPC/cluster ladění<br />-Integrované ladění více jazyků<br />– Ladění vzájemné spolupráce<br />– Ladění za běhu<br />– Místní ladění<br />– Spravované ladění<br />-Manual Control (okno procesů)<br />– Paměť<br />– Podpora S minimálním výpisem<br />– Moduly<br />– Ladění více procesů<br />– Nativní ladění<br />– Nová podpora ladicího stroje<br />– Ladění optimalizovaného kódu<br />-Output Filtering Windows<br />– Proces hostování pro spravované ladění<br />– Procesy<br />– QuickWatch<br />-Registry<br />– Registruje se v zásobníku.<br />– Vzdálené ladění<br />– Návratové hodnoty<br />-Ladění skriptů<br />– Podpora zdrojové služby<br />– Zabezpečení<br />– Vedle sebe<br />– SQL<br />– Symbol server<br />– Body trasování<br />– Vlákno<br />– Vizualizace<br />– Ladicí program XSLT (Extensible Stylesheet Language Transforming)|  
|64-bitová podpora|-64-bitové ladění pro spravovaný i nativní kód, všechny jazyky<br />– x64 – nativní podpora|  
|Správa zdrojového kódu (SCC)|– Základní integrace SCC. Viz Poznámka 3.<br />– Ověřování nástrojů a možností|  
|Rozšiřitelnost|– Využívání VSPackage a komponent MEF|  
  
## <a name="notes"></a>Poznámky  
  
#### <a name="1-data-tools"></a>1. Data Tools  
 Integrované prostředí zahrnuje nástroje pro vývoj databází, jako je podpora rozšíření dat a zjednodušená **Průzkumník řešení**. Sestavy SQL Server Express, SQL Reporting a Crystal však nejsou součástí integrovaného prostředí.  
  
#### <a name="2-debugging-support"></a>2. Podpora ladění  
 Integrované prostředí obsahuje stejný ladicí stroj, který je součástí komunity verze sady Visual Studio. Ladicí stroj obsahuje společný ladicí program pro spravovaný kód a také související funkce, jako je spuštění, připojení, nastavení zarážky, úpravy a pokračování a další. Modul ladění však nepodporuje SQL Server ladění databáze.  
  
 I když je podpora nativního ladění součástí balíčku základního ladicího programu, nemůžete ji zvětšit na podporu dalších jazyků.  
  
#### <a name="3-source-code-control-integration"></a>3. integrace správy zdrojového kódu  
 Integrované prostředí poskytuje rozhraní API pro implementaci ovládacího prvku SCC (Source-Code Control) a pro poskytování komponent pro integraci společného řízení zdrojů založeného na MSSCCI.  
  
 I když integrace SCC není běžnou funkcí edice pro sady Visual Studio, integrace SCC je poskytována v integrovaném prostředí.  
  
#### <a name="4-build-support"></a>4. podpora sestavení  
 Integrované prostředí poskytuje podporu sestavení. Informace o sestaveních najdete v [referenčních](../msbuild/msbuild-reference.md)informacích k MSBuild.  
  
## <a name="features-not-included-in-the-integrated-shell"></a>Funkce, které nejsou zahrnuté v integrovaném prostředí  
 V následujícím seznamu najdete funkce, které nejsou zahrnuté do integrovaného prostředí:  
  
- Návrhář tříd  
  
- PreEmptive ochranu – řešení Dotfuscator  
  
- Jazykové funkce  
  
- VSHost  
  
- V integrovaném prostředí shell nejsou zahrnuté žádné jazyky sady Visual Studio ani jejich přidružené šablony projektů ani šablony položek projektu. Nejsou k dispozici žádné implementace žádného konkrétního jazyka pro jiné funkce, například Visual Basic fragmenty kódu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled rozšíření sady Visual Studio](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)
