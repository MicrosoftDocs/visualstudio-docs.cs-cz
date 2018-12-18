---
title: Řešení potíží s odkazy na služby | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 90ec170182d0b54e6185de68f5ca03a5e114f0ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223956"
---
# <a name="troubleshooting-service-references"></a>Řešení potíží s odkazy na služby
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Toto téma obsahuje seznam běžných problémů, které mohou nastat při práci s [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] nebo [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] odkazuje v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="error-returning-data-from-a-service"></a>Chyba vrácení dat ze služby
 Po návratu `DataSet` nebo `DataTable` ze služby, může se zobrazit výjimka "kvóta maximální velikosti příchozích zpráv došlo k překročení". Ve výchozím nastavení `MaxReceivedMessageSize` pro některé vazby je nastavena na hodnotu poměrně málo početnému omezit vystavení útokům odmítnutí služby. Zvýšíte tuto hodnotu, aby se zabránilo výjimku.

 Chcete-li vyřešit tuto chybu:

1.  V **Průzkumníka řešení**, poklikejte na soubor app.config a otevře jej.

2.  Vyhledejte `MaxReceivedMessageSize` vlastnosti a změňte ji na vyšší hodnotu.

## <a name="cannot-find-a-service-in-my-solution"></a>Nelze najít službu v mém řešení
 Po kliknutí **zjišťování** tlačítko **přidat odkazy na služby** dialogové okno, jeden nebo více projektů knihovny služby WCF v řešení se nezobrazují v seznamu služeb. Tato situace může nastat, pokud knihovna služby byl přidán do řešení, ale nebyl dosud zkompilována.

 Chcete-li vyřešit tuto chybu:

-   V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt knihovny služby WCF a klikněte na tlačítko **sestavení**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Chyba při přístupu ke službě přes vzdálenou plochu
 Když uživatel pracuje s WCF hostované webové služby přes připojení ke vzdálené ploše a uživatel nemá oprávnění správce, bude použito ověřování NTLM. Pokud uživatel nemá oprávnění správce, uživatel může zobrazit následující chybová zpráva: "požadavek HTTP Neoprávněný se schématem autorizace klienta"Anonymní". Záhlaví ověření přijaté ze serveru byla: NTLM"."

 Chcete-li vyřešit tuto chybu:

1.  V projektu webové stránky, otevřete **vlastnosti** stránky.

2.  Na **možnosti spuštění** kartu, zrušte **ověřování protokolem NTLM** zaškrtávací políčko.

    > [!NOTE]
    > Měli byste vypnout ověřování protokolem NTLM pouze pro webové stránky, které obsahují výhradně služby WCF. Zabezpečení služeb WCF je spravována prostřednictvím konfigurace v souboru web.config. Díky ověřování protokolem NTLM zbytečné.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Úroveň přístupu pro vygenerované třídy nastavení nemá žádný vliv
 Nastavení **přístup k úrovni pro vygenerované třídy** možnost **nakonfigurovat odkazy na služby** dialogové okno **interní** nebo **Friend** vždy nemusí fungovat. Přestože možnost se zobrazí v dialogovém okně, výsledné třídy podpory se vygeneruje s úrovní přístupu `Public`.

 Jedná se o známé omezení určitých typů, jako jsou ty serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Chyba ladění kódu služby
 Při krokování s vnořením kód služby WCF v kódu klienta, můžete obdržet chybu související s chybějící symboly. Tato situace může nastat, když služba, která byla součástí vašeho řešení se přesunout nebo odebrán z řešení.

 Když je nejprve přidat odkaz na službu WCF, která je součástí aktuálního řešení, přidá se explicitní závislost sestavení mezi projekt služby a projekt služby klienta. Zaručí se tak, že klient vždy přistupuje k binární soubory aktuální služby, který je obzvláště důležité pro ladění scénářů, jako je například krokování kódu služby z klientského kódu.

 Pokud projekt služby je odebrán z řešení, tato závislost explicitní sestavení je neplatná. Visual Studio již nemůže zaručit, že je znovu sestavit projekt služby podle potřeby.

 Chcete-li tuto chybu vyřešit, budete muset ručně znovu sestavit projekt služby:

1.  Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.

2.  V **možnosti** dialogového okna rozbalte **projekty a řešení**a pak vyberte **Obecné**.

3.  Ujistěte se, že **zobrazit pokročilé konfigurace sestavení** zaškrtávací políčko zaškrtnuto a pak klikněte na **OK**.

4.  Načtěte projekt služby WCF. Další informace najdete v tématu [NIB postupy: vytváření řešení vícenásobného projektu](http://msdn.microsoft.com/en-us/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).

5.  V **nástroje Configuration Manager** dialogové okno, nastavte **konfigurace aktivního řešení** k **ladění**. Další informace najdete v tématu [postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md).

6.  V **Průzkumníka řešení**, vyberte projekt služby WCF.

7.  Na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit** znovu sestavit projekt služby WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>Služby WCF Data Services nezobrazují v prohlížeči
 Když se pokusí zobrazit reprezentaci XML dat [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], může aplikace Internet Explorer chybně interpretovat data jako informační kanál RSS. Zkontrolujte, zda je zakázána možnost zobrazení informačních kanálů RSS.

 Chcete-li vyřešit tuto chybu, zakažte informační kanály RSS:

1.  V Internet Exploreru na **nástroje** nabídky, klikněte na tlačítko **Možnosti Internetu**.

2.  Na **obsahu** kartě **informační kanály** klikněte na tlačítko **nastavení**.

3.  V **nastavení informačního kanálu** dialogové okno, zrušte **zapnout zobrazení pro čtení informačního kanálu** zaškrtněte políčko a potom klikněte na tlačítko **OK**.

4.  Klikněte na tlačítko **OK** zavřete **Možnosti Internetu** dialogové okno.

## <a name="see-also"></a>Viz také:

- [Služby Windows Communication Foundation a služby WCF Data Services v sadě Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)