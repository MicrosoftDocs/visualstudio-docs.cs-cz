---
title: Visual Studio Emulator for Android | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 28d82c13273f18f9787104f080ed39c9c903076c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884833"
---
# <a name="visual-studio-emulator-for-android"></a>Emulátor sady Visual Studio pro Android

Visual Studio Emulator for Android je desktopová aplikace, které emuluje zařízení s Androidem. Poskytuje virtualizované prostředí, ve kterém můžete ladit a testovat aplikace pro Android bez fyzického zařízení. Také poskytuje izolované prostředí pro vaše aplikace prototypů.  

> [!IMPORTANT]
> Ve většině scénářů si emulátor Google Android se doporučuje namísto emulátor Visual Studia pro Android:
> - Visual Studio Emulator for Android není podporována po sadu Visual Studio 2015.
> - – Image emulátorů novější než verze systému Android 6.0 nejsou k dispozici pro Visual Studio Emulator for Android.
> - Emulátor Google Android teď podporuje [Hyper-V](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration#hyper-v).
> - Visual Studio Tools for Apache Cordova spolupracuje s emulátor Google Android. Další informace najdete v tématu [spuštění aplikace Apache Cordova v Androidu](/visualstudio/cross-platform/tools-for-cordova/run-your-app/run-app-android#google-android-emulator) (Všimněte si, že už máte zakázat Hyper-V, jak je popsáno v tomto článku).
>
> Další informace o konfiguraci a použití emulátoru Google Android najdete v tématu [instalace emulátoru Androidu](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/).
  
 Visual Studio Emulator for Android je navržené pro poskytování srovnatelné výkonu pro skutečné zařízení. Předtím, než můžete publikovat aplikaci, doporučujeme však, že testujete aplikaci na fyzickém zařízení.  
  
 Testovat svou aplikaci na profil jedinečné zařízení pro jednotlivé platformy Android, rozlišení obrazovky a dalších vlastností hardwaru – nepodporuje emulátor Visual Studia pro Android.
  
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
  
- [Požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
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
  
 ![Emulátor sady Visual Studio pro správce sady Android](../cross-platform/media/android_emu_manager.png "Android_Emu_Manager")  
  
 Ve výchozím nastavení, k dispozici jsou čtyři předem nainstalovaných zařízení profily (KitKat a Lollipop phone/5 "a tabletu/7" Konfigurace), jak je uvedeno bílý text a ikony. Další profily v seznamu zobrazí šedě, dokud se nerozhodnete **instalace profilu** tlačítko a instalace se dokončí. Můžete filtrovat seznam podle úrovně rozhraní API a klikněte na šipku podrobností v dolní pravé části profilu zobrazíte její podrobnosti úplná konfigurace.  
  
 Po instalaci sady profilů, které chcete cílit, lze tyto nové profily spustit stisknutím zelené přímo ze správce **Přehrát** tlačítko. Zobrazí se také v rozevírací nabídce Cíl ladění do libovolného typu – multiplatformního mobilního projektu sady Visual Studio.  
  
##  <a name="FeaturesTest"></a> Funkce, které můžete testovat se spustila v emulátoru  
 Podrobné informace o funkcích můžete otestovat v emulátoru, najdete v tomto [blogový příspěvek](https://blogs.msdn.microsoft.com/devops/2014/11/12/introducing-visual-studios-emulator-for-android/).  
  
##  <a name="FeaturesNonTest"></a> Funkce, které nelze otestovat v emulátoru  
 Následující seznam popisuje funkce platformy Android, které jste **nelze** testování se spustila v emulátoru. Máte k testování těchto funkcí na fyzickém zařízení.  
  
-   Compass  
  
-   Volný setrvačník  
  
-   Vibrace kontroleru  
  
-   Jas. Změna jasu úrovně emulátoru nebude mít vliv na vizuální způsob, jakým se zařízení zobrazí na obrazovce.  
  
##  <a name="Support"></a> Informační zdroje podpory  
 Pokud hostitelský počítač splňuje požadavky na systém a narazíte na problém, která nejsou zahrnuta do tohoto průvodce odstraňováním potíží:  
  
-   Položit dotaz na StackOverflow pomocí [emulátor android](http://stackoverflow.com/questions/tagged/android-emulator) a značku visual studio.  
  
-   Nahlaste problém pomocí odeslat úsměv nástroje v sadě Visual Studio nebo v správce emulátoru.  
  
## <a name="see-also"></a>Viz také:  
 [Požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
