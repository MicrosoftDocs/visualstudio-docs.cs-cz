---
title: Řešení potíží s rozšířením VSPackages | Dokumentace Microsoftu
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
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b2c9a7b57a8b15683cb202b71e33e908a1bfd1b5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764010"
---
# <a name="troubleshooting-vspackages"></a>Řešení potíží s rozšířením VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tady jsou běžné problémy, které může mít s vaší VSPackage a tipy pro řešení problémů.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Řešení potíží s VSPackage, která zajišťuje spuštění sady Visual Studio  
  
-   Spustit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v nouzovém režimu.  
  
     Chcete-li spustit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v nouzovém režimu, na příkazovém řádku, zadejte **/safemode devenv.exe**.  
  
     Během tohoto procesu jsou načteny žádné balíčky VSPackages, s výjimkou rozšíření VSPackages, které jsou součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Řešení potíží s VSPackage, která se nenačte  
  
1.  Ujistěte se, že používáte kořenový klíč registru, ve které je zaregistrovaný sady VSPackage ke spuštění, obvykle kořenový klíč registru experimentální.  
  
     Další informace najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
2.  Pokud sady VSPackage cílí na spouštění v kořenovém adresáři registru experimentální, ujistěte se, že spustíte experimentální verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Chcete-li spustit experimentální verzi, zadejte následující příkaz v příkazovém okně: **devenv /rootsuffix exp**.  
  
3.  Zkontrolujte položky registru VSPackage.  
  
     Další informace najdete v tématu [registrace rozšíření VSPackages](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd) a [Správa balíčky VSPackages](../extensibility/managing-vspackages.md).  
  
4.  Otevřít **výstup** okno instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , které se nedaří načíst sady VSPackage. Informace o proč sady VSPackage nedaří se načíst může být zobrazen v tomto okně.  
  
    > [!NOTE]
    >  Pokud začínáte experimentální verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrované vývojové prostředí (IDE), zkontrolujte **výstup** okno obě verze.  
  
5.  Vyhledejte v protokolu aktivit.  
  
     Další informace najdete v tématu [postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).  
  
6.  Další informace o výjimky vyvolané z integrovaného vývojového prostředí, klikněte na tlačítko **výjimky** na **ladění** nabídka umožňující výjimky. V **výjimky** dialogové okno Vybrat typy výjimek, které chcete získat další informace.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Řešení potíží s VSPackage, která nezaregistruje  
  
1.  Ujistěte se, že VSPackage sestavení se nachází v důvěryhodném umístění. RegPkg nejde zaregistrovat sestavení v částečně důvěryhodných nebo nedůvěryhodných umístění, například sdílené síťové složky ve výchozí konfiguraci zabezpečení rozhraní .net. I když se upozornění zobrazí vždycky, když uživatel vytvoří projekt v nedůvěryhodném umístění, můžete toto upozornění nevyskytla zabránit zaškrtávací políčko "tuto zprávu znovu nezobrazovat".  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Řešení potíží s příkaz, který není viditelný, nebo po kliknutí na příkaz, který generuje chybu  
  
1.  Sloučit příkazy nabídky nové nebo změněné. ti se již v integrovaném vývojovém prostředí pomocí následujícího příkazu na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] příkazového řádku: **/rootsuffix devenv/Setup Exp**.  
  
2.  Ujistěte se, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] UI.dll vyhledat vašeho balíčku VSPackage.  
  
    1.  Identifikátor CLSID sady VSPackage najdete v části balíčků z registru:  
  
         HKLM\Software\Microsoft\Visual Studio\\*\<verze >* \Packages  
  
    2.  Ověřte správnost cesty Dal podklíč SatelliteDll.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Řešení potíží s, který se chová neočekávaně VSPackage  
  
1.  Nastavte zarážky v kódu.  
  
     Dobrým výchozím bodem pro ladění jsou konstruktor a inicializační metoda. Můžete také nastavit zarážky v oblasti, kterou chcete vyhodnotit, například příkaz nabídky. Pokud chcete povolit zarážky, je nutné spustit v ladicím programu.  
  
    1.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
    2.  Na **stránky vlastností** dialogové okno, vyberte **ladění** kartu.  
  
    3.  V **argumenty příkazového řádku** zadejte příponu kořenové vývojového prostředí, které vaše cíle VSPackage. Pokud chcete vybrat experimentální sestavení, zadejte například: **RootSuffix Exp**.  
  
    4.  Na **ladění** nabídky, klikněte na tlačítko **spustit ladění** nebo stiskněte klávesu F5.  
  
        > [!NOTE]
        >  Když provádíte ladění projektu, vytvořit nebo načíst existující instanci projektu nyní.  
  
2.  Použití protokolu aktivit.  
  
     Sledujte chování balíčku VSPackage pomocí zápisu informací do protokolu aktivit se zapsaly klíčové body. Tato technika je užitečná při spuštění v prostředí maloobchodu VSPackage. Další informace najdete v tématu [postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).  
  
3.  Použití veřejných symbolů.  
  
     Aby se zlepšila čitelnost při ladění, můžete připojit symboly v ladicím programu.  
  
    1.  Z **Nástroje/možnosti** nabídky, přejděte **ladění/symboly** dialogové okno.  
  
    2.  Přidejte tuto **Symbol umístění souboru souborů (.pdb)**:  
  
         [http://msdl.microsoft.com/download/symbols](http://msdl.microsoft.com/download/symbols)  
  
    3.  Ke zlepšení výkonu, zadejte složku mezipaměti symbolů, například:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Řešení potíží s chybějící VSPackage nebo některá z jeho závislostí  
  
1. Pro spravovaný kód Ujistěte se, že cesty odkazů jsou správné.  
  
   1.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
   2.  Vyberte **odkazy** kartu **stránky vlastností** dialogové okno a ujistěte se, že všechny cesty mají správný. Alternativně můžete použít **prohlížeče objektů** a vyhledejte odkazované objekty.  
  
        Pro spravovaný kód, můžete použít [Fuslogvw.exe (Assembly Binding Log Viewer)](http://msdn.microsoft.com/library/e32fa443-0778-4cc3-bf36-5c8ea297d296) zobrazíte podrobnosti o načtení sestavení se nezdařilo.  
  
2. Nespravovaný kód, najít identifikátor CLSID VSPackage v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uzlu registru CLSID:  
  
    HKLM\Software\Microsoft\Visual Studio\\*\<verze >* \CLSID  
  
   Ujistěte se, že položka InprocServer32 má správnou cestu knihovny dll balíčku VSPackage.  
  
## <a name="see-also"></a>Viz také  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)

