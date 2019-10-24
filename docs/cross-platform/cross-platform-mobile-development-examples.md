---
title: Příklady vývoje mobilních aplikací pro různé platformy | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bc384c12-fccc-45d7-9fb9-b90d536aa663
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 8eb8b53da30f0c0896ac9576407d34f9a2f9bdbc
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777713"
---
# <a name="cross-platform-mobile-development-examples"></a>Příklady vývoje multiplatformních mobilních řešení

Některé z šablon nainstalovaných **mobilním vývojem s C++**  využitím úlohy generují kompletní příklady, ze kterých můžete získat informace. Centrum vývojářů pro Windows navíc obsahuje několik ukázkových aplikací, které si můžete stáhnout a vyzkoušet v aplikaci Visual Studio.

- [Ukázka aplikace Hello-JNI pro Android](https://code.msdn.microsoft.com/hello-jni-Android-790ab73d)

   Tato ukázka je portem aplikace NDK Hello-JNI pro Android. Ukázka demonstruje ucelenou aplikaci Java Native Interface "Hello World". Načte řetězec z nativní metody implementované ve sdílené knihovně a pak ho zobrazí v aplikaci.

- [Ukázka aplikace Hello-gl2 pro Android](https://code.msdn.microsoft.com/hello-gl2-Android-3b61896c)

   Tato ukázka je portem aplikace NDK Hello-gl2 pro Android. Ukázka demonstruje komplexní aplikaci OpenGL pro nativní rozhraní Java Native Interface. Vykreslí trojúhelník pomocí rozhraní API OpenGL ES 2,0 shader.

- [Ukázka rastrového obrázku plazmy pro Android](https://code.msdn.microsoft.com/Bitmap-Plasma-Android-77ae296a)

   Tato ukázka je portem aplikace plazmy pro NDK rastrového obrázku pro Android. Ukázka demonstruje komplexní aplikaci Java Native Interface Android ES 2,0. Ukazuje přímou manipulaci s vyrovnávacími pamětmi rastrového obrázku Androidu pro generování plazmového efektu.

- [Ukázka knihovny TwoLibs pro Android](https://code.msdn.microsoft.com/TwoLibs-Android-Library-6396e5c4)

   Tato ukázka je portem ukázky Android NDK TwoLibs. Používá dynamicky načtenou sdílenou knihovnu a statickou C++ nativní knihovnu Android, která implementuje metodu volanou z aplikace Java Native Interface. Tato ukázka je dobrým výchozím bodem pro vývojáře, který vám pomůže pochopit, jak používat statické a dynamické sdílené knihovny k sestavení komplexní aplikace JNI pro Android pomocí sady Visual Studio.

- [Ukázka aplikace pro Android pot](https://code.msdn.microsoft.com/Tea-Pot-Android-Application-e7c05d73)

   Tato ukázka je portem aplikace pro Android NDK konvice. Ukázka demonstruje komplexní aplikaci Java Native Interface Android ES 2,0.

- [Ukázka aplikace MoreTeaPots pro Android](https://code.msdn.microsoft.com/MoreTeaPots-Android-a9bd8549)

   Tato ukázka je portem aplikace pro Android NDK MoreTeaPots. Ukázka demonstruje komplexní aplikaci OpenGL pro nativní rozhraní Java Native Interface.

- [Ukázka knihovny Android test-libstdcpp](https://code.msdn.microsoft.com/test-libstdcpp-Android-00b548f5)

   Tato ukázka je portem ukázky Android NDK test-libstdc + +, konkrétně pro použití se sadou Visual Studio. Tato ukázka je dobrým výchozím bodem pro vývojáře, který vám pomůže pochopit, jak používat standardní knihovnu.

  Chcete-li otevřít jeden z příkladů v aplikaci Visual Studio, Stáhněte soubor zip a otevřete stránku **vlastnosti** staženého souboru v Průzkumníkovi. Zvolte tlačítko **odblokování** a pak zvolte **OK**. Extrahujte obsah souboru zip do vhodného umístění, pak otevřete C++ složku v extrahované ukázce a otevřete soubor řešení.

  Chcete-li vytvořit ukázku, stiskněte klávesu **F7**nebo na panelu nabídek zvolte možnost **sestavit**, **Sestavit řešení**.
