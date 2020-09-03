---
title: Řešení potíží s odkazy na služby | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60f06aa64cf6a6b96f0c4d610fba1d20b794c55f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667199"
---
# <a name="troubleshooting-service-references"></a>Řešení potíží s odkazy na služby
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Toto téma obsahuje seznam běžných problémů, ke kterým může dojít při práci s nástrojem [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] nebo [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] v tématu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="error-returning-data-from-a-service"></a>Chyba při vracení dat ze služby
 Když vrátíte `DataSet` nebo `DataTable` ze služby, může se zobrazit výjimka "kvóta maximální velikosti pro příchozí zprávy byla překročena". Ve výchozím nastavení `MaxReceivedMessageSize` je vlastnost pro některé vazby nastavená na relativně malou hodnotu, aby se omezilo riziko útoků na dostupnost služby. Tuto hodnotu můžete zvýšit, chcete-li zabránit výjimce.

 Oprava této chyby:

1. V **Průzkumník řešení**dvakrát klikněte na soubor app.config a otevřete ho.

2. Vyhledejte `MaxReceivedMessageSize` vlastnost a změňte ji na větší hodnotu.

## <a name="cannot-find-a-service-in-my-solution"></a>V řešení nejde najít službu.
 Když v dialogovém okně **Přidat odkazy na službu** kliknete na tlačítko **Vyhledat** , v seznamu služby se nezobrazí jeden nebo více projektů knihovny služby WCF v řešení. Tato situace může nastat, pokud byla do řešení přidána Knihovna služby, ale ještě nebyla zkompilována.

 Oprava této chyby:

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt knihovny služby WCF a klikněte na **sestavit**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Chyba při přístupu ke službě přes vzdálenou plochu
 Když uživatel přistupuje ke službě WCF hostované na webu přes připojení ke vzdálené ploše a uživatel nemá oprávnění správce, bude použito ověřování NTLM. Pokud uživatel nemá oprávnění správce, může se uživateli zobrazit následující chybová zpráva: "požadavek HTTP je neautorizovaný se schématem ověřování klienta" anonymous ". Ověřovací hlavička přijatá ze serveru byla "NTLM". "

 Oprava této chyby:

1. V projektu webu otevřete stránky **vlastností** .

2. Na kartě **Možnosti spuštění** zrušte zaškrtnutí políčka **ověřování NTLM** .

    > [!NOTE]
    > Ověřování NTLM byste měli vypnout jenom pro weby, které obsahují výhradně služby WCF. Zabezpečení služeb WCF je spravováno pomocí konfigurace v souboru web.config. Ověřování protokolem NTLM je zbytečné.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Nastavení úrovně přístupu pro vygenerované třídy nemá žádný vliv.
 Nastavení možnosti **úroveň přístupu pro vygenerované třídy** v dialogovém okně **konfigurovat odkazy na služby** na **interní** nebo **přítel** nemusí vždy fungovat. I když se v dialogovém okně zobrazí možnost nastavená, výsledné podpůrné třídy budou vygenerovány s úrovní přístupu `Public` .

 Toto je známé omezení určitých typů, například serializovaných pomocí <xref:System.Xml.Serialization.XmlSerializer> .

## <a name="error-debugging-service-code"></a>Chyba při ladění kódu služby
 Při kroku do kódu služby WCF z klientského kódu se může zobrazit chyba související s chybějícími symboly. Tato situace může nastat, pokud byla služba, která byla součástí vašeho řešení, přesunuta nebo odebrána z řešení.

 Při prvním přidání odkazu na službu WCF, která je součástí aktuálního řešení, je přidána explicitní závislost sestavení mezi projektem služby a projektem klienta služby. To zaručuje, že klient vždy přistupuje k aktuálním binárním souborům služby, což je obzvláště důležité pro scénáře ladění, jako je například krokování z kódu klienta do kódu služby.

 Pokud je projekt služby odebrán z řešení, je zrušena platnost této explicitní závislosti sestavení. Visual Studio již nemůže zaručit, že projekt služby bude znovu sestaven podle potřeby.

 Chcete-li tuto chybu opravit, je nutné ručně znovu sestavit projekt služby:

1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).

2. V dialogovém okně **Možnosti** rozbalte položku **projekty a řešení**a pak vyberte možnost **Obecné**.

3. Ujistěte se, že je zaškrtnuté políčko **Zobrazit pokročilou konfiguraci sestavení** , a pak klikněte na **OK**.

4. Načtěte projekt služby WCF. Další informace naleznete v tématu [NIB How to: Create Multi-Project Solutions](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).

5. V dialogovém okně **Configuration Manager** nastavte **konfiguraci aktivního řešení** na **ladit**. Další informace najdete v tématu [Postup: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md).

6. V **Průzkumník řešení**vyberte projekt služby WCF.

7. V nabídce **sestavení** klikněte na znovu **sestavit** a znovu sestavte projekt služby WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services se nezobrazují v prohlížeči
 Když se pokusí zobrazit XML reprezentace dat v aplikaci [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] , Internet Explorer může data interpretovat jako informační kanál RSS. Zkontrolujte, zda je zakázána možnost zobrazení informačních kanálů RSS.

 Pokud chcete tuto chybu opravit, zakažte kanály RSS:

1. V aplikaci Internet Explorer v nabídce **nástroje** klikněte na možnost **Možnosti Internetu**.

2. Na kartě **obsah** v části **informační kanály** klikněte na **Nastavení**.

3. V dialogovém okně **Nastavení informačního kanálu** zrušte zaškrtnutí políčka **zapnout zobrazení pro čtení informačního kanálu** a potom klikněte na tlačítko **OK**.

4. Kliknutím na tlačítko **OK** zavřete dialogové okno **Možnosti Internetu** .

## <a name="see-also"></a>Viz také

- [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)