---
title: Emulátor sady Visual Studio pro Android | Microsoft Docs
ms.custom: ''
ms.prod: visual-studio-dev15
ms.date: 02/13/2020
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 73dd10cf1923caa6703acc0ef9d4fde82c13f5bb
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272034"
---
# <a name="visual-studio-emulator-for-android"></a>Emulátor sady Visual Studio pro Android

Emulátor sady Visual Studio pro Android je desktopová aplikace, která emuluje zařízení s Androidem. Poskytuje virtualizované prostředí, ve kterém můžete ladit a testovat aplikace pro Android bez fyzického zařízení. Poskytuje také izolované prostředí pro prototypy vaší aplikace.

> [!IMPORTANT]
> Ve většině scénářů se emulátor Google Android doporučuje použít místo emulátoru sady Visual Studio pro Android:
> - Emulátor sady Visual Studio pro Android není podporován po aplikaci Visual Studio 2015.
> - Image emulátoru novější než Android verze 6,0 nejsou k dispozici pro emulátor sady Visual Studio pro Android.
> - Google Android Emulator teď podporuje [Hyper-V](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration#accelerating-with-hyper-v).
> - Visual Studio Tools pro Apache Cordova spolupracuje s Android Emulator Google. Další informace najdete v tématu [spuštění aplikace Apache Cordova v Androidu](/visualstudio/cross-platform/tools-for-cordova/run-your-app/run-app-android#google-android-emulator) (Všimněte si, že už nemusíte zakázat technologii Hyper-V, jak je popsáno v tomto článku).
>
> Další informace o konfiguraci a používání služby Google Android Emulator najdete v tématu [Android Emulator Setup](/xamarin/android/get-started/installation/android-emulator/).

 Emulátor sady Visual Studio pro Android je navržený tak, aby poskytoval srovnatelný výkon pro skutečné zařízení. Před publikováním aplikace však doporučujeme otestovat aplikaci na fyzickém zařízení.

 Svou aplikaci můžete testovat v jedinečném profilu zařízení pro jednotlivé platformy Android, rozlišení obrazovky a další vlastnosti hardwaru podporované emulátorem sady Visual Studio pro Android.

## <a name="Installing"></a>Instalace a odinstalace
 Instalace

 Emulátor sady Visual Studio pro Android je součástí nástrojů pro různé platformy, které jsou dostupné v aplikaci Visual Studio a bude se instalovat během vlastního nastavení sady Visual Studio, když vyberete mobilní vývoj pro různé platformy, pak běžné nástroje a sady pro vývoj softwaru. a potom emulátor sady Visual Studio pro Android.

 Odinstalace

 Emulátor sady Visual Studio pro Android můžete odinstalovat pomocí ovládacího panelu Přidat nebo odebrat programy.

> [!NOTE]
> Odinstalace sady Visual Studio neodinstaluje emulátor neproběhne. Emulátor musíte odinstalovat samostatně.

 Po odinstalaci emulátoru sady Visual Studio pro Android se virtuální adaptéry pro virtuální počítače Hyper-V, které byly vytvořeny pro emulátor pro použití, automaticky neodeberou. Tyto virtuální adaptéry (Pokud se nepoužívají) můžete ručně odebrat tak, že otevřete Správce technologie Hyper-V, vyberete jednu z imagí VHD emulátoru, kliknete na kartu síť a zvolíte **Odebrat** pro všechny přepínače, které se zobrazí na této kartě.

## <a name="Requirements"></a>Požadavky na systém a zpětná kompatibilita
 Důležité informace o požadavcích na hardware, software a konfiguraci pro emulátor sady Visual Studio pro Android najdete v následujícím tématu.

- [Požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

  Emulátor sady Visual Studio pro Android vyžaduje Visual Studio 2015; není zpětně kompatibilní se staršími verzemi sady Visual Studio.

  Nové verze emulátoru se instalují na staré verze (a můžou v některých případech nahradit staré image a zahozením nastavení, aplikací a souborů nainstalovaných na těchto obrázcích.

## <a name="Networking"></a>Sítě v emulátoru sady Visual Studio pro Android
 Síťové připojení emulátoru sady Visual Studio pro Android se chová jako připojení stolního počítače s těmito charakteristikami:

- Emulátor se zobrazí v síti jako samostatné zařízení s vlastní IP adresou.

- Nevyžaduje žádný další síťový software, který ještě není nainstalovaný s emulátorem.

- Není připojen k doméně systému Windows.

  Aby bylo možné pochopit možnosti síťového připojení emulátoru, zamyslete se nad tím, jak připojení Wi-Fi z telefonu s Androidem do stejné sítě. Pokud má aplikace spuštěná v telefonu přístup k síťovému prostředku přes připojení k síti Wi-Fi, může aplikace spuštěná v emulátoru také přistupovat ke stejnému síťovému prostředku.

  Další informace o požadavcích sítě najdete v tématu [požadavky na systém pro emulátor sady Visual Studio pro Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  Informace o řešení problémů se sítí najdete v tématu [Poradce při potížích s emulátorem sady Visual Studio pro Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).

## <a name="Configuring"></a>Konfigurace emulátoru sady Visual Studio pro Android
 Testování kompatibility aplikace pro Android v rámci nejrůznějšího spektra hardwaru s Androidem může být náročné. Telefony a tablety s Androidem na trhu mají široké spektrum verzí a velikostí obrazovky a přicházejí v mnoha různých konfiguracích hardwaru (RAM, procesorech, architektuře atd.). Emulátor sady Visual Studio pro Android ho zjednodušuje pomocí profilů zařízení. Naše sada profilů zařízení představuje nejoblíbenější hardware na trhu, včetně zařízení od společnosti Samsung, Motorola, Sony, LG a dalších.

 V aplikaci Visual Studio 2015 můžete nainstalovat, odinstalovat a spustit profily zařízení pomocí Správce emulátoru. Přístup ke Správci emulátoru můžete vybrat tak, že vyberete **nástroje**a potom **emulátor sady Visual Studio pro Android**.

 ![Emulátor sady Visual Studio pro Android Manager](../cross-platform/media/android_emu_manager.png "Android_Emu_Manager")

 Ve výchozím nastavení jsou nainstalovány čtyři předem nainstalované profily zařízení (konfigurace KitKat a lupy Phone/5 a tablet/7), které jsou označeny prázdným textem a ikonami. Ostatní profily v seznamu se zobrazí šedě, dokud nekliknete na tlačítko **instalovat profil** a instalace skončí. Seznam můžete filtrovat podle úrovně rozhraní API a kliknutím na šipku podrobností v pravém dolním rohu profilu zobrazit jeho úplné podrobnosti o konfiguraci.

 Po instalaci sady profilů, na kterou chcete cílit, můžete spustit tyto nové profily přímo z správce stisknutím zeleného tlačítka **Přehrát** . Zobrazí se také v rozevírací nabídce cíl ladění v libovolném typu mobilního projektu pro různé platformy sady Visual Studio.

## <a name="FeaturesTest"></a>Funkce, které můžete testovat v emulátoru
 Podrobné informace o funkcích, které můžete testovat v emulátoru, najdete v tomto [blogovém příspěvku](https://devblogs.microsoft.com/devops/introducing-visual-studios-emulator-for-android/).

## <a name="FeaturesNonTest"></a>Funkce, které nemůžete testovat v emulátoru
 Následující seznam popisuje funkce platformy Android, které **nemůžete** testovat v emulátoru. Tyto funkce je nutné testovat na fyzickém zařízení.

- Kompas

- Gyroskop

- Kontroler vibrací

- Světlost. Změna úrovně jasu emulátoru nebude vizuálně ovlivňovat způsob, jakým se zařízení zobrazuje na obrazovce.

## <a name="Support"></a>Prostředky podpory
 Pokud hostitelský počítač splňuje požadavky na systém a narazíte na problém, která nejsou zahrnuta do tohoto průvodce odstraňováním potíží:

- Položte otázku na StackOverflow pomocí [emulátoru Androidu](https://stackoverflow.com/questions/tagged/android-emulator) a sady Visual Studio.

- Nahlaste problém pomocí odeslat úsměv nástroje v sadě Visual Studio nebo v správce emulátoru.

## <a name="see-also"></a>Viz také
 [Požadavky na systém pro emulátor sady Visual Studio pro](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) [řešení potíží s emulátorem sady Visual Studio pro](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md) Android
