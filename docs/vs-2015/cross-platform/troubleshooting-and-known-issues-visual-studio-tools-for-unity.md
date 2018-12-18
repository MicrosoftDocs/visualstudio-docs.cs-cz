---
title: Řešení potíží a známé problémy (Visual Studio Tools for Unity) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 94240d5af43944b23890a32b757fe1b4f14b77ec
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755519"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Odstraňování potíží a známé problémy (Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
V této části vám najít řešení běžných potíží s nástroji Visual Studio Tools for Unity, popis známých problémů a zjistěte, jak můžete pomoci zvýšit zpráv o chybách Visual Studio Tools for Unity.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Chcete-li vyřešit některé běžné problémy s Visual Studio Tools for Unity, naleznete v následujících částech.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrace z UnityVS pro Visual Studio Tools for Unity  
 Pokud migrujete z UnityVS pro Visual Studio Tools for Unity, budete muset vytvořit nové řešení sady Visual Studio pro své projekty Unity.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>K migraci z UnityVS 1.8 svým projektem Unity pro Visual Studio Tools pro Unity 1.9  
  
1.  Odstraňte staré soubory řešení a projektu z Unity projektu. V kořenovém adresáři vašeho projektu Unity, vyhledejte Visual Studio .sln a. * proj soubory a odstraňte je všechny.  
  
2.  Visual Studio Tools for Unity balíček naimportujte Unity projektu. Informace o tom, jak importovat balíček VSTU najdete v tématu Konfigurace Visual Studio Tools for Unity na [Začínáme](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) stránky.  
  
3.  Generovat nové soubory řešení a projektu. Pokud chcete vygenerovat teď v Unity editoru v hlavní nabídce zvolte **Visual Studio Tools**, **Generovat soubory projektu**. V opačném případě můžete tento krok přeskočit, pokud chcete zjistit. Visual Studio Tools for Unity vygeneruje nové soubory automaticky při výběru **Visual Studio Tools**, **otevřít v sadě Visual Studio**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio se nenačte řešení, které vytvoří Visual Studio Tools for Unity  
 Další informace najdete v tématu [odpověď na tuto otázku stackoverflow](http://stackoverflow.com/a/24035907/36702).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>V systému Windows 8 Visual Studio výzvu ke stažení Cílová architektura Unity  
 UnityVS vyžaduje rozhraní .net framework 3.5, který není nainstalovaný ve výchozím nastavení v systému Windows 8. Chcete-li vyřešit tento problém, postupujte podle pokynů ke stažení a instalaci rozhraní .net framework 3.5.  
  
## <a name="known-issues"></a>Známé problémy  
 Jsou známy problémy ve Visual Studio Tools for Unity, které jsou výsledkem způsobu interakce ladicí program Unity a starší verzi kompilátoru jazyka C#. Pracujeme na řešení těchto problémů, ale do té doby může dojít k následujícím problémům.  
  
-   Při ladění Unity někdy dojde k chybě.  
  
-   Při ladění, se zablokuje někdy Unity.  
  
-   Krokování do proměnné a z metody v některých případech se chová nesprávně, zejména v iterátory nebo v rámci příkazů přepínače.  
  
## <a name="reporting-errors"></a>Hlášení chyb  
 Pomozte nám zlepšovat kvalitu Visual Studio Tools for Unity odesíláním zpráv o chybách, když dochází k chybám, zablokuje nebo jiné chyby. To pomáhá nám prozkoumat a řešit problémy ve Visual Studio Tools for Unity. Děkuju!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak ohlásit chybu, když Visual Studio zamrzne  
 Existují sestavy, které Visual Studio zamrzne někdy při ladění pomocí Visual Studio Tools for Unity, ale potřebujeme víc dat, abyste pochopili tento problém. Pomůžete nám prozkoumat pomocí následujících kroků.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Pro sestavu, která sadě Visual Studio se zablokuje při ladění se sadou Visual Studio Tools for Unity  
  
1. Otevřete novou instanci sady Visual Studio.  
  
2. Otevřete dialogu připojit k procesu. V nové instanci sady Visual Studio, v hlavní nabídce zvolte **ladění**, **připojit k procesu**.  
  
3. Připojte ladicí modul k zmrazené instanci sady Visual Studio. V **připojit k procesu** dialogového okna, vyberte zmrazené instanci sady Visual Studio z **procesy k dispozici** tabulku a pak zvolte **připojit** tlačítko.  
  
4. Pozastavte ladicí program. V nové instanci sady Visual Studio, v hlavní nabídce zvolte **ladění**, **příkaz Pozastavit vše** nebo stačí stisknout kombinaci kláves **Ctrl + Alt + Break**.  
  
5. Vytvoření výpisu podprocesu. V příkazovém řádku zadejte následující příkaz a stiskněte klávesu **Enter**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Možná budete muset provést **příkaz** okno viditelné první. V sadě Visual Studio, zvolte v hlavní nabídce **zobrazení**, **ostatní Windows**, **příkazové okno**.  
  
6. Nakonec odešlete výpisu vlákna do [ vstusp@microsoft.com ](mailto:vstusp@microsoft.com), spolu s popis co jste dělali při začal být zmrazené sady Visual Studio.

