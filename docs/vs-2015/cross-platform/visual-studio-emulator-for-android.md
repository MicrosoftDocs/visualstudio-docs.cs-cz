---
title: Visual Studio Emulator for Android | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: 22126bb5a364148c7079d59d750483a7ebc47418
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799593"
---
# <a name="visual-studio-emulator-for-android"></a>Emulátor sady Visual Studio pro Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Visual Studio Emulator for Android je desktopová aplikace, které emuluje zařízení s Androidem. Poskytuje virtualizované prostředí, ve kterém můžete ladit a testovat aplikace pro Android bez fyzického zařízení. Také poskytuje izolované prostředí pro vaše aplikace prototypů.  
  
 Visual Studio Emulator for Android je navržené pro poskytování srovnatelné výkonu pro skutečné zařízení. Předtím, než můžete publikovat aplikaci, doporučujeme však, že testujete aplikaci na fyzickém zařízení.  
  
 Testovat svou aplikaci na profil jedinečné zařízení pro jednotlivé platformy Android, rozlišení obrazovky a dalších vlastností hardwaru – nepodporuje emulátor Visual Studia pro Android.  
  
 Toto téma obsahuje následující části.  
  
-   [Instalace a odinstalace](#Installing)  
  
-   [Požadavky na systém a zpětné kompatibility](#Requirements)  
  
-   [Správa sítě v sadě Visual Studio Emulator for Android](#Networking)  
  
-   [Konfigurace Visual Studio Emulator for Android](#Configuring)  
  
-   [Funkce, které můžete testovat se spustila v emulátoru](#FeaturesTest)  
  
-   [Funkce, které nelze otestovat v emulátoru](#FeaturesNonTest)  
  
-   [Informační zdroje podpory](#Support)  
  
##  <a name="Installing"></a> Instalace a odinstalace  
 Instalace  
  
 Visual Studio Emulator for Android je součástí nástrojů pro různé platformy k dispozici v sadě Visual Studio a je možné nainstalovat během vlastní instalační program sady Visual Studio, když vyberete Cross-Platform Mobile Development, potom společné nástroje a Software Development Kit a pak Visual Studio Emulator for Android.  
  
 Odinstalace  
  
 Odinstalovat Visual Studio Emulator pro Android pomocí panelu Přidat nebo odebrat programy v Ovládacích panelech.  
  
> [!NOTE]
>  Odinstalace sady Visual Studio nedojde k odinstalování emulátoru. Emulátor je nutné odinstalovat samostatně.  
  
 Když odinstalujete Visual Studio Emulator pro Android, technologie Hyper-V virtuální sítě Ethernet adaptéry, které byly vytvořeny pro emulátor používat automaticky neodeberou. Můžete ručně odebrat tyto virtuální adaptéry (Pokud nepoužíváte) otevřete Správce technologie Hyper-V, výběrem některé z imagí virtuálního pevného disku emulátor, výběrem karty sítě a zvolením **odebrat** všech přepínačích, které se zobrazí na této kartě.  
  
##  <a name="Requirements"></a> Požadavky na systém a zpětné kompatibility  
 Důležité informace o hardwaru, softwaru a požadavky na konfiguraci pro emulátor sady Visual Studio pro Android najdete v následujícím tématu.  
  
- [Systémové požadavky pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Vyžaduje Visual Studio 2015; Visual Studio Emulator for Android není zpětně kompatibilní s předchozími verzemi sady Visual Studio.  
  
  Nové verze emulátoru se nainstalovat navíc k samotnému starší verze (a v některých případech může nahradit původní bitové kopie se zahodí nastavení, aplikace a soubory, které jsou nainstalované v těchto imagí).  
  
##  <a name="Networking"></a> Správa sítě v sadě Visual Studio Emulator for Android  
 Síťové připojení emulátor Visual Studia pro Android se chová jako připojení aplikace stolním počítači s těmito charakteristikami:  
  
- Emulátor se jeví jako samostatný zařízení pomocí jeho vlastní IP adresu v síti.  
  
- Nevyžaduje žádné další síťový software, který ještě není nainstalovaná s emulátorem.  
  
- Není připojený k doméně Windows.  
  
  Informace o tom možnosti připojení k síti na emulátor, si ho přemýšlejte jako podobný připojení Wi-Fi z telefonu s Androidem ke stejné síti. Aplikace běžící na vašem telefonu můžete získat přístup k síťovému prostředku přes Wi-Fi připojení, potom aplikaci spuštěnou v emulátoru dostanete také stejný prostředek sítě.  
  
  Další informace o požadavky na sítě, naleznete v tématu [požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  Informace o řešení potíží s problémy se sítí najdete v tématu [řešení potíží s Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Configuring"></a> Konfigurace Visual Studio Emulator for Android  
 Testování vaší aplikace pro Android z důvodu kompatibility odstupňování nejrůznějších Android hardware může být složité. Android telefonech a tabletech na trhu span širokou škálu verze a velikostí obrazovky a pak v mnoha různých hardwarové konfigurace (paměti RAM, procesory, architektury, atd.). Visual Studio Emulator for Android tím zjednodušuje, pomocí profilů zařízení. Naše sada profilů zařízení představuje neoblíbenější hardware na trhu, včetně zařízení Samsung, Motorola, Sony, LG a dalších.  
  
 V sadě Visual Studio 2015 můžete nainstalovat, odinstalujte a spustit profily zařízení pomocí Správce emulátorů. Přístup správce emulátorů výběrem **nástroje**, pak **Visual Studio Emulator for Android**.  
  
 ![Emulátor sady Visual Studio pro správce sady Android](../cross-platform/media/android-emu-manager.png "Android_Emu_Manager")  
  
 Ve výchozím nastavení, k dispozici jsou čtyři předem nainstalovaných zařízení profily (KitKat a Lollipop phone/5 "a tabletu/7" Konfigurace), jak je uvedeno bílý text a ikony. Další profily v seznamu zobrazí šedě, dokud se nerozhodnete **instalace profilu** tlačítko a instalace se dokončí. Můžete filtrovat seznam podle úrovně rozhraní API a klikněte na šipku podrobností v dolní pravé části profilu zobrazíte její podrobnosti úplná konfigurace.  
  
 Po instalaci sady profilů, které chcete cílit, lze tyto nové profily spustit stisknutím zelené přímo ze správce **Přehrát** tlačítko. Zobrazí se také v rozevírací nabídce Cíl ladění do libovolného typu – multiplatformního mobilního projektu sady Visual Studio.  
  
##  <a name="FeaturesTest"></a> Funkce, které můžete testovat se spustila v emulátoru  
 Podrobné informace o funkcích můžete otestovat v emulátoru, najdete v tomto [dokumentaci](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx).  
  
##  <a name="FeaturesNonTest"></a> Funkce, které nelze otestovat v emulátoru  
 Následující seznam popisuje funkce platformy Android, které jste **nelze** testování se spustila v emulátoru. Máte k testování těchto funkcí na fyzickém zařízení.  
  
-   Kompas  
  
-   Gyroskop  
  
-   Vibrace kontroleru  
  
-   Jas. Změna jasu úrovně emulátoru nebude mít vliv na vizuální způsob, jakým se zařízení zobrazí na obrazovce.  
  
##  <a name="Support"></a> Informační zdroje podpory  
 Pokud hostitelský počítač splňuje požadavky na systém a narazíte na problém, která nejsou zahrnuta do tohoto průvodce odstraňováním potíží:  
  
-   Položit dotaz na StackOverflow pomocí [emulátor android](http://stackoverflow.com/questions/tagged/android-emulator) a značku visual studio.  
  
-   Nahlaste problém pomocí odeslat úsměv nástroje v sadě Visual Studio nebo v správce emulátoru.  
  
## <a name="see-also"></a>Viz také  
 [Požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)

