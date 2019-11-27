---
title: Řešení potíží a známé problémy (Visual Studio Tools for Unity) | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: ad085cc6c41714a551fbb344274e6d0f164ab67e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297664"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Odstraňování potíží a známé problémy (Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V této části vám najít řešení běžných potíží s nástroji Visual Studio Tools for Unity, popis známých problémů a zjistěte, jak můžete pomoci zvýšit zpráv o chybách Visual Studio Tools for Unity.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Pokud chcete vyřešit některé běžné problémy s Visual Studio Tools for Unity, přečtěte si následující oddíly.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrace z UnityVS na Visual Studio Tools for Unity  
 Pokud migrujete z UnityVS na Visual Studio Tools for Unity, budete muset vygenerovat nová řešení sady Visual Studio pro projekty Unity.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Migrace projektu Unity z UnityVS 1,8 na Visual Studio Tools for Unity 1,9  
  
1. Odstraňte ze svého projektu Unity staré soubory řešení a projektu. V kořenovém adresáři vašeho projektu Unity vyhledejte soubory Visual Studio. sln a. * proj a odstraňte je.  
  
2. Importujte balíček Visual Studio Tools for Unity do projektu Unity. Informace o tom, jak importovat balíček VSTU, najdete v tématu Konfigurace Visual Studio Tools for Unity na stránce [Začínáme](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  
  
3. Vygenerujte nové soubory řešení a projektu. Pokud je chcete vygenerovat nyní, v editoru Unity v hlavní nabídce vyberte možnost **Visual Studio Tools**, **Generovat soubory projektu**. V opačném případě můžete tento krok přeskočit, pokud chcete; Visual Studio Tools for Unity vygeneruje nové soubory automaticky, když vyberete **Visual Studio Tools** **otevřete v aplikaci Visual Studio**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio nenačte řešení, které Visual Studio Tools for Unity vytvořené.  
 Další informace najdete v [odpovědi na tuto StackOverflow otázku](https://stackoverflow.com/questions/20086755/unityvs-visual-studio-can-not-open/24035907#24035907).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>Ve Windows 8 se Visual Studio zeptá na stažení cílové architektury Unity.  
 UnityVS vyžaduje rozhraní .NET Framework 3,5, které není ve výchozím nastavení nainstalované ve Windows 8. Chcete-li tento problém vyřešit, postupujte podle pokynů ke stažení a instalaci rozhraní .NET Framework 3,5.  
  
## <a name="known-issues"></a>Známé problémy  
 Jsou známy problémy ve Visual Studio Tools for Unity, které jsou výsledkem způsobu interakce ladicí program Unity a starší verzi kompilátoru jazyka C#. Pracujeme na tom, abychom vám pomohli tyto problémy vyřešit, ale mezitím se můžete setkat s následujícími problémy.  
  
- Při ladění Unity někdy dojde k chybě.  
  
- Při ladění, se zablokuje někdy Unity.  
  
- Krokování do proměnné a z metody v některých případech se chová nesprávně, zejména v iterátory nebo v rámci příkazů přepínače.  
  
## <a name="reporting-errors"></a>Hlášení chyb  
 Pomozte nám zlepšovat kvalitu Visual Studio Tools for Unity odesíláním zpráv o chybách, když dochází k chybám, zablokuje nebo jiné chyby. To pomáhá nám prozkoumat a řešit problémy ve Visual Studio Tools for Unity. Děkuju!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Jak ohlásit chybu, když Visual Studio zamrzne  
 Existují sestavy, které Visual Studio zamrzne někdy při ladění pomocí Visual Studio Tools for Unity, ale potřebujeme víc dat, abyste pochopili tento problém. Pomůžete nám prozkoumat pomocí následujících kroků.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Pro sestavu, která sadě Visual Studio se zablokuje při ladění se sadou Visual Studio Tools for Unity  
  
1. Otevřete novou instanci sady Visual Studio.  
  
2. Otevřete dialogu připojit k procesu. V hlavní nabídce v nové instanci aplikace Visual Studio vyberte možnost **ladit**, **připojit k procesu**.  
  
3. Připojte ladicí modul k zmrazené instanci sady Visual Studio. V dialogovém okně **připojit k procesu** vyberte zmrazenou instanci sady Visual Studio z tabulky **Dostupné procesy** a pak klikněte na tlačítko **připojit** .  
  
4. Pozastavte ladicí program. V nové instanci aplikace Visual Studio v hlavní nabídce zvolte možnost **ladit**, **přerušit vše** nebo pouze stiskněte **kombinaci kláves CTRL + ALT + BREAK**.  
  
5. Vytvoření výpisu podprocesu. V okno Příkaz zadejte následující příkaz a stiskněte klávesu **ENTER**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Může být nutné okno **příkazového** řádku zviditelnit jako první. V aplikaci Visual Studio v hlavní nabídce vyberte možnost **zobrazení**, **ostatní**okna, **příkazové okno**.  
  
6. Nakonec pošlete výpis vlákna [vstusp@microsoft.com](mailto:vstusp@microsoft.com)společně s popisem toho, co jste dělali při zmrazení sady Visual Studio.
