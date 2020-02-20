---
title: Řešení potíží s VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- VSPackages, troubleshooting
- debugging, VSPackages
ms.assetid: 274673e7-72e7-476f-a263-3411b5b874be
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b092c910b0303a62289e75b168e39628cbd0314b
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476996"
---
# <a name="troubleshooting-vspackages"></a>Řešení potíží s rozšířením VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Níže jsou uvedené běžné problémy, se kterými se můžete setkat se sadou VSPackage a tipy k řešení těchto problémů.  
  
### <a name="to-troubleshoot-a-vspackage-that-keeps-visual-studio-from-starting"></a>Řešení potíží VSPackage, který brání spuštění sady Visual Studio  
  
- Spusťte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v nouzovém režimu.  
  
     Chcete-li spustit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v nouzovém režimu, zadejte do příkazového řádku **devenv. exe/safemode**.  
  
     Během tohoto procesu nejsou načteny žádné sady VSPackage s výjimkou VSPackage, které jsou součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-load"></a>Řešení potíží s VSPackage, který se nenačte  
  
1. Ujistěte se, že používáte kořen registru, ve kterém je rozhraní VSPackage registrováno pro spuštění, obvykle pro experimentální kořen registru.  
  
     Další informace najdete v [experimentální instanci](../extensibility/the-experimental-instance.md).  
  
2. Pokud je rozhraní VSPackage cíleno na spuštění v kořenovém adresáři experimentálního registru, ujistěte se, že používáte experimentální verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Chcete-li spustit experimentální verzi, zadejte následující příkaz v příkazovém okně: **devenv/rootsuffix exp**.  
  
3. Ověřte položky registru VSPackage.  
  
     Další informace najdete v tématu [Registrace VSPackage](internals/registering-vspackages.md) a [Správa VSPackage](../extensibility/managing-vspackages.md).  
  
4. Otevřete okno **výstup** instance [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], který nedaří načíst VSPackage. Informace o tom, proč se rozhraní VSPackage nedaří načíst, může být zobrazeno v tomto okně.  
  
    > [!NOTE]
    > Pokud spouštíte experimentální verzi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrovaného vývojového prostředí (IDE), zkontrolujte okno **výstup** obou verzí.  
  
5. Projděte si protokol aktivit.  
  
     Další informace najdete v tématu [Postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).  
  
6. Další informace o výjimkách vyvolaných rozhraním IDE získáte tak, že kliknete na **výjimky** v nabídce **ladění** a povolíte výjimky. V dialogovém okně **výjimky** vyberte typy výjimek, o kterých chcete získat další informace.  
  
### <a name="to-troubleshoot-a-vspackage-that-does-not-register"></a>Řešení potíží s VSPackage, který se neregistruje  
  
1. Ujistěte se, že se sestavení VSPackage nachází v důvěryhodném umístění. RegPkg nemůže registrovat sestavení v nedůvěryhodném nebo částečně důvěryhodném umístění, například v síťové sdílené složce ve výchozí konfiguraci zabezpečení .NET. I když se zobrazí upozornění pokaždé, když uživatel vytvoří projekt v nedůvěryhodném umístění, zaškrtávací políčko znovu nezobrazovat tuto zprávu může zabránit opětovnému výskytu tohoto upozornění.  
  
### <a name="to-troubleshoot-a-command-that-is-not-visible-or-that-generates-an-error-when-you-click-a-command"></a>Řešení potíží s příkazem, který není viditelný nebo který při kliknutí na příkaz vygeneruje chybu  
  
1. Slučte nové nebo změněné příkazy nabídky a těch, které jsou již v integrovaném vývojovém prostředí, zadáním následujícího příkazu na příkazovém řádku [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]: **devenv/rootsuffix exp/Setup**.  
  
2. Ujistěte se, že [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] najít UI. dll pro VSPackage.  
  
    1. Vyhledejte CLSID sady VSPackage v oddílu Packages v registru:  
  
         HKLM\Software\Microsoft\Visual Studio\\ *\<verze >* \Packages  
  
    2. Ověřte, zda je cesta daného podklíče SatelliteDll správná.  
  
### <a name="to-troubleshoot-a-vspackage-that-behaves-unexpectedly"></a>Řešení potíží s VSPackage, který se chová neočekávaně  
  
1. Nastavte zarážky v kódu.  
  
     Dobrým počátečním bodem pro ladění jsou konstruktor a inicializační metoda. Můžete také nastavit zarážky v oblasti, kterou chcete vyhodnotit, jako je například příkaz nabídky. Chcete-li povolit zarážky, je nutné spustit v ladicím programu.  
  
    1. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
    2. V dialogovém okně **stránky vlastností** vyberte kartu **ladění** .  
  
    3. V poli **argumenty příkazového řádku** zadejte kořenovou příponu vývojového prostředí, které vaše rozhraní VSPackage cílí. Chcete-li například vybrat experimentální sestavení, zadejte: **/rootsuffix exp**.  
  
    4. V nabídce **ladění** klikněte na příkaz **Spustit ladění** nebo stiskněte klávesu F5.  
  
        > [!NOTE]
        > Pokud ladíte projekt, vytvořte nebo Načtěte existující instanci projektu nyní.  
  
2. Použijte protokol aktivit.  
  
     Sledujte chování VSPackage zápisem informací do protokolu aktivit v klíčových bodech. Tato technika je užitečná hlavně při spuštění sady VSPackage v maloobchodním prostředí. Další informace najdete v tématu [Postupy: použití protokolu aktivit](../extensibility/how-to-use-the-activity-log.md).  
  
3. Používejte veřejné symboly.  
  
     Pro zlepšení čitelnosti při ladění můžete k ladicímu programu připojit symboly.  
  
    1. V nabídce **Nástroje/možnosti** přejděte do dialogového okna **ladění/symboly** .  
  
    2. Přidat toto **umístění souboru se symboly (. pdb)** :  
  
         `https://msdl.microsoft.com/download/symbols`  
  
    3. Chcete-li zvýšit výkon, zadejte složku mezipaměti symbolů, například:  
  
        ```  
        C:\symbols  
        ```  
  
### <a name="to-troubleshoot-a-missing-vspackage-or-one-of-its-dependencies"></a>Řešení potíží s chybějícím VSPackage nebo některou z jeho závislostí  
  
1. Pro spravovaný kód zkontrolujte, zda jsou cesty odkazů správné.  
  
   1. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
   2. V dialogovém okně **stránky vlastností** vyberte kartu **odkazy** a ujistěte se, že jsou všechny cesty správné. Alternativně můžete použít **Prohlížeč objektů** k procházení odkazovaných objektů.  
  
        Pro spravovaný kód můžete použít [Fuslogvw. exe (Prohlížeč protokolu vazby sestavení)](https://msdn.microsoft.com/library/e32fa443-0778-4cc3-bf36-5c8ea297d296) k zobrazení podrobností o neúspěšném načtení sestavení.  
  
2. Pro nespravovaný kód vyhledejte identifikátor CLSID sady VSPackage v uzlu registru [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CLSID:  
  
    HKLM\Software\Microsoft\Visual Studio\\ *\<verze >* \CLSID  
  
   Ujistěte se, že položka InprocServer32 má správnou cestu k knihovně VSPackage dll.  
  
## <a name="see-also"></a>Viz také  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)
