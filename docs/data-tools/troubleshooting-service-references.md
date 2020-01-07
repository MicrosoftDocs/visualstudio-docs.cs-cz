---
title: Řešení potíží s odkazy na služby
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d52562382f10615c7da1dfab22d4c18323b725b3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586117"
---
# <a name="troubleshoot-service-references"></a>Řešení potíží s odkazy na služby

Toto téma obsahuje seznam běžných problémů, ke kterým může dojít při práci s Windows Communication Foundation (WCF) nebo WCF Data Services odkazy v aplikaci Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Chyba při vracení dat ze služby

Když vrátíte `DataSet` nebo `DataTable` ze služby, může se zobrazit výjimka "kvóta maximální velikosti pro příchozí zprávy byla překročena". Ve výchozím nastavení je vlastnost `MaxReceivedMessageSize` pro některé vazby nastavená na relativně malou hodnotu, aby se omezilo riziko útoků DOS (Denial-of-Service). Tuto hodnotu můžete zvýšit, chcete-li zabránit výjimce. Další informace najdete v tématu <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Chcete-li vyřešit tuto chybu:

1. V **Průzkumník řešení**dvakrát klikněte na soubor *App. config* a otevřete ho.

2. Vyhledejte vlastnost `MaxReceivedMessageSize` a změňte ji na větší hodnotu.

## <a name="cannot-find-a-service-in-my-solution"></a>V řešení nejde najít službu.

Když v dialogovém okně **Přidat odkazy na službu** kliknete na tlačítko **Vyhledat** , v seznamu služby se nezobrazí jeden nebo více projektů knihovny služby WCF v řešení. Tato situace může nastat, pokud byla do řešení přidána Knihovna služby, ale ještě nebyla zkompilována.

Chcete-li vyřešit tuto chybu:

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt knihovny služby WCF a klikněte na **sestavit**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Chyba při přístupu ke službě přes vzdálenou plochu

Když uživatel přistupuje ke službě WCF hostované na webu přes připojení ke vzdálené ploše a uživatel nemá oprávnění správce, bude použito ověřování NTLM. Pokud uživatel nemá oprávnění správce, může se uživateli zobrazit následující chybová zpráva: "požadavek HTTP je neautorizovaný se schématem ověřování klienta" anonymous ". Ověřovací hlavička přijatá ze serveru byla "NTLM". "

Chcete-li vyřešit tuto chybu:

1. V projektu webu otevřete stránky **vlastností** .

2. Na kartě **Možnosti spuštění** zrušte zaškrtnutí políčka **ověřování NTLM** .

    > [!NOTE]
    > Ověřování NTLM byste měli vypnout jenom pro weby, které obsahují výhradně služby WCF. Zabezpečení služeb WCF je spravováno prostřednictvím konfigurace v souboru *Web. config* . Ověřování protokolem NTLM je zbytečné.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Nastavení úrovně přístupu pro vygenerované třídy nemá žádný vliv.

Nastavení možnosti **úroveň přístupu pro vygenerované třídy** v dialogovém okně **konfigurovat odkazy na služby** na **interní** nebo **přítel** nemusí vždy fungovat. I když se v dialogovém okně objeví možnost nastavená, výsledné podpůrné třídy se generují s úrovní přístupu `Public`.

Toto je známé omezení určitých typů, například serializovaných pomocí <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Chyba při ladění kódu služby

Při kroku do kódu služby WCF z klientského kódu se může zobrazit chyba související s chybějícími symboly. Tato situace může nastat, pokud byla služba, která byla součástí vašeho řešení, přesunuta nebo odebrána z řešení.

Při prvním přidání odkazu na službu WCF, která je součástí aktuálního řešení, je přidána explicitní závislost sestavení mezi projektem služby a projektem klienta služby. To zaručuje, že klient vždy přistupuje k aktuálním binárním souborům služby, což je obzvláště důležité pro scénáře ladění, jako je například krokování z kódu klienta do kódu služby.

Pokud je projekt služby odebrán z řešení, je zrušena platnost této explicitní závislosti sestavení. Visual Studio již nemůže zaručit, že projekt služby bude znovu sestaven podle potřeby.

Chcete-li tuto chybu opravit, je nutné ručně znovu sestavit projekt služby:

1. Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.

2. V dialogovém okně **Možnosti** rozbalte položku **projekty a řešení**a pak vyberte možnost **Obecné**.

3. Ujistěte se, že je zaškrtnuté políčko **Zobrazit pokročilou konfiguraci sestavení** , a pak klikněte na **OK**.

4. Načtěte projekt služby WCF.

5. V dialogovém okně **Configuration Manager** nastavte **konfiguraci aktivního řešení** na **ladit**. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md).

6. V **Průzkumník řešení**vyberte projekt služby WCF.

7. V nabídce **sestavení** klikněte na znovu **sestavit** a znovu sestavte projekt služby WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services se nezobrazují v prohlížeči

Když se pokusí zobrazit XML reprezentace dat v [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], Internet Explorer může data interpretovat jako informační kanál RSS. Ujistěte se, že je zakázaná možnost Zobrazit kanály RSS.

Pokud chcete tuto chybu opravit, zakažte kanály RSS:

1. V aplikaci Internet Explorer v nabídce **nástroje** klikněte na možnost **Možnosti Internetu**.

2. Na kartě **obsah** v části **informační kanály** klikněte na **Nastavení**.

3. V dialogovém okně **Nastavení informačního kanálu** zrušte zaškrtnutí políčka **zapnout zobrazení pro čtení informačního kanálu** a potom klikněte na tlačítko **OK**.

4. Kliknutím na tlačítko **OK** zavřete dialogové okno **Možnosti Internetu** .

## <a name="see-also"></a>Viz také:

- [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
