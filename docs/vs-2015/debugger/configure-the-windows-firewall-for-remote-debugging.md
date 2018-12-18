---
title: Konfigurace brány Windows Firewall pro vzdálené ladění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39854b47bd31660fdc523bfd122363d5958df8e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51734587"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Konfigurace brány Windows Firewall pro vzdálené ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje postup konfigurace brány firewall pro povolení vzdáleného ladění na počítačích, na kterých běží tyto operační systémy:  
  
- Windows 7  
  
- Windows 8 nebo 8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 R2  
  
  Pokud v síti, na kterém jsou ladění není chráněné bránou firewall, tato konfigurace je zbytečné. V opačném případě počítače, který je hostitelem aplikace Visual Studio a vzdáleného počítače, který má být laděn vyžadovat změny konfigurace brány firewall.  
  
  **Protokol IPSec** Pokud síť vyžaduje tuto komunikaci se provádí pomocí protokolu IPSec, je nutné otevřít další porty na hostitelském počítači Visual Studio, tak vzdálenému počítači.  
  
  **Webový Server** Pokud ladíte vzdáleného webového serveru, je nutné otevřít další port na vzdáleném počítači.  
  
  Všimněte si, že oba počítače nemají běžet stejný operační systém. Například v počítači s Visual Studio můžete spustit Windows 10 a vzdáleného počítače můžete spustit systém Windows Server 2012 R2.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>Konfigurace brány Windows Firewall v počítači aplikace Visual Studio  
 Pokyny ke konfiguraci brány Windows firewall se mírně liší v různých operačních systémech. Na Windows 7 nebo Windows Server 2008, slovo **program** slouží; v systému Windows 8 a 8.1, Windows 10 a Windows Server 2012, slovo **aplikace** se používá.  V následujícím postupu použijeme slovo **aplikace**.  
  
1.  Otevřete stránku brány Windows Firewall. (V **Start** nabídky vyhledávacího pole, typ **brány Windows Firewall**).  
  
2.  Klikněte na tlačítko **povolit aplikaci nebo funkci průchod bránou Windows Firewall**.  
  
3.  V **povolené aplikace a funkce** seznamu, vyhledejte **Visual Studio vzdálený ladicí program zjišťování**. Pokud je hodnota uvedena, ujistěte se, že je vybraná a že budou vybrány také jeden nebo více typů sítě.  
  
4.  Pokud **Visual Studio vzdálený ladicí program zjišťování** není uvedená, klikněte na **jiné aplikace bude**. Pokud stále nevidíte ji v **přidat aplikaci** okna, klikněte na tlačítko **Procházet** a přejděte do  **\<instalačního adresáře sady Visual Studio > \Common7\IDE\Remoteladicíhoprogramu**. Vyhledejte příslušnou složku pro aplikaci (x86, x64 Appx) a pak vyberte **msvsmon.exe**. Pak klikněte na tlačítko **přidat**.  
  
5.  V **povolené aplikace a funkce** seznamu vyberte **Visual Studio Remote Debugging Monitor**. Zkontrolujte jeden nebo více typů sítě (**domény, domů a do práce (privátní), veřejné**), který má sledování vzdáleného ladění pro komunikaci s. Typy musí zahrnovat sítě, ke kterému je připojený počítač Visual Studio.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>Pro otevření portu v počítači aplikace Visual Studio povolit zjišťování  
 Musíte také povolit port UDP 3702 příchozí povolit zjišťování počítače spuštění vzdáleného ladicího programu. Přidat, najdete v tématu Postup konfigurace portů v bráně Firewall.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>Konfigurace brány Windows firewall vzdáleného počítače pro vzdálené ladění  
 Komponenty vzdáleného ladění můžete nainstalovaný na vzdáleném počítači nebo spustit ze sdíleného adresáře. V obou případech musí být nakonfigurované brány firewall vzdáleném počítači. Komponenty vzdáleného ladění se nacházejí v:  
  
 **\<Visual Studio Instalační adresář > \Common7\IDE\Remote ladicího programu**  
  
 Pokyny ke konfiguraci brány Windows firewall se mírně liší v různých operačních systémech. Na Windows 7 nebo Windows Server 2008, slovo **program** slouží; v systému Windows 8 a 8.1, Windows 10 a Windows Server 2012, slovo **aplikace** se používá.  V následujícím postupu použijeme slovo **aplikace**.  
  
1.  Otevřete stránku brány Windows Firewall. (Na **Start** nabídky vyhledávacího pole, typ **brány Windows Firewall**.)  
  
2.  Klikněte na tlačítko **povolit aplikaci nebo funkci průchod bránou Windows Firewall**.  
  
3.  V **povolené aplikace a funkce** seznamu, vyhledejte **Visual Studio Remote Debugging Monitor**. Pokud je hodnota uvedena, ujistěte se, že je vybraná a že budou vybrány také jeden nebo více typů sítě.  
  
4.  Pokud **Visual Studio Remote Debugging Monitor** není uvedená, klikněte na **jiné aplikace bude**. Pokud stále nevidíte ji v **přidat oknem aplikace**, klikněte na tlačítko **Procházet** a přejděte do  **\<instalačního adresáře sady Visual Studio > \Common7\IDE\Remoteladicíhoprogramu**. Vyhledejte příslušnou složku pro aplikaci (x86, x64 Appx) a pak vyberte **msvsmon.exe**. Pak klikněte na tlačítko **přidat**.  
  
5.  V **povolené aplikace** seznamu vyberte **Visual Studio Remote Debugging Monitor**. Zkontrolujte jeden nebo více typů sítě (**domény, domů a do práce (privátní), veřejné**), který má sledování vzdáleného ladění pro komunikaci s. Typy musí zahrnovat sítě, ke kterému je připojený počítač Visual Studio.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porty na vzdáleném počítači, které umožňují vzdálené ladění  
  
|||||  
|-|-|-|-|  
|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|  
|3702|Odchozí|UDP|Vyžaduje se pro zjišťování vzdálený ladicí program.|  
|4020||TCP|Pro VS 2015. Číslo portu je zvýšen o 2 pro každou verzi sady Visual Studio. Další informace najdete v tématu Visual Studio vzdálené přiřazení portů ladicího programu.|  
|4021||TCP|Pro VS 2015. Číslo portu je zvýšen o 2 pro každou verzi sady Visual Studio. Další informace najdete v tématu Visual Studio vzdálené přiřazení portů ladicího programu.|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>Porty na vzdáleném počítači, které umožňují vzdálené ladění v režimu kompatibility spravované nebo nativní  
  
|||||  
|-|-|-|-|  
|**Porty**|**Příchozí/odchozí**|**Protokol**|**Popis**|  
|135, 139, 445|Odchozí|TCP|Požadováno.|  
|137, 138|Odchozí|UDP|Požadováno.|  
|500, 4500|Odchozí|UDP|Povinné, pokud zásady vaší domény vyžadují síťové komunikace, která se má provést prostřednictvím protokolu IPSec.|  
|80|Odchozí|TCP|Vyžaduje se pro ladění webového serveru.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Postup konfigurace portů v bráně Windows Firewall  
  
1.  Na **Start** nabídky, vyhledejte **brány Windows Firewall s pokročilým zabezpečením**.  
  
2.  Klikněte na tlačítko **příchozí pravidla** nebo **odchozí pravidla** a potom klikněte na tlačítko **nové pravidlo** v **akce** seznamu.  
  
3.  Na **typ pravidla** stránce **Port** a potom klikněte na tlačítko **Další**.  
  
4.  Na **protokol a porty** stránky, vyberte protokol, port (TCP nebo UDP). Vyberte **určité místní porty** a zadejte jednu nebo více čísla portů, které chcete povolit protokol. Oddělovače číslic čárkami. Pak klikněte na tlačítko **Další**.  
  
5.  Na **akce** stránce **povolit připojení** a potom klikněte na tlačítko **Další**.  
  
6.  Na **profilu** vyberte jeden nebo více typů sítě pro povolení portu. Typ, který jste vybrali musí zahrnovat sítě, ke kterému je připojený vzdáleného počítače. Pak klikněte na tlačítko **Další**.  
  
7.  Na **název** stránky, zadejte název pravidla a potom klikněte na tlačítko **Dokončit**.  
  
8.  Měli byste vidět nové pravidlo v **příchozí pravidla** nebo **odchozí pravidla** seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)



