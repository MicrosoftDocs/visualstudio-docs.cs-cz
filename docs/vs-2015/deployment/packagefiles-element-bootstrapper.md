---
title: '&lt;PackageFiles – &gt; element (zaváděcí nástroj) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 382689dada13adce1ee530e66fef6ba78452efaa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188983"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles – &gt; element (zaváděcí nástroj)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`PackageFiles`Element obsahuje `PackageFile` prvky, které definují instalační balíčky provedené jako výsledek `Command` elementu.  
  
## <a name="syntax"></a>Syntax  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## <a name="elements-and-attributes"></a>Elementy a atributy  
 `PackageFiles`Element má následující atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|Nepovinný parametr. Pokud je nastaveno na `false` , instalační program stáhne pouze soubory, na které se odkazuje z `Command` elementu. Pokud je nastaveno na `true` , budou staženy všechny soubory.<br /><br /> Pokud je nastaveno na `IfNotHomesite` , instalační program bude fungovat stejně, jako kdyby `False` `ComponentsLocation` byl nastaven na hodnotu `HomeSite` a jinak se bude chovat stejně jako if `True` . Toto nastavení může být užitečné, pokud chcete, aby balíčky, které jsou vlastními zavaděči, mohly ve scénáři HomeSite spustit své vlastní chování.<br /><br /> Výchozí formát je `true`.|  
  
## <a name="packagefile"></a>PackageFile  
 `PackageFile`Prvek je podřízeným prvkem `PackageFiles` elementu. `PackageFiles`Element musí mít alespoň jeden `PackageFile` element.  
  
 `PackageFile` má následující atributy.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Name`|Povinná hodnota. Název souboru balíčku. Jedná se o název, který `Command` prvek bude odkazovat, pokud definuje podmínky, za kterých se balíček nainstaluje. Tato hodnota se používá také jako klíč do `Strings` tabulky pro načtení lokalizovaného názvu, který nástroje, jako je například, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] používá k popisu balíčku.|  
|`HomeSite`|Nepovinný parametr. Umístění balíčku na vzdáleném serveru, pokud není součástí instalačního programu.|  
|`CopyOnBuild`|Nepovinný parametr. Určuje, zda má zaváděcí nástroj zkopírovat soubor balíčku na disk v okamžiku sestavení. Výchozí hodnota je true.|  
|`PublicKey`|Zašifrovaný veřejný klíč podepsaného certifikátu balíčku. Vyžaduje `HomeSite` se, pokud se používá; jinak volitelné.|  
|`Hash`|Nepovinný parametr. Hodnota hash SHA1 souboru balíčku. Slouží k ověření integrity souboru v době instalace. Pokud se identická hodnota hash nedá vypočítat ze souboru balíčku, balíček se nenainstaluje.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje balíčky pro [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Distribuovatelný balíček a jeho závislosti, například instalační služba systému Windows.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<Product> Objekt](../deployment/product-element-bootstrapper.md)   
 [\<Package> Objekt](../deployment/package-element-bootstrapper.md)   
 [Referenční schéma balíčku a produktu](../deployment/product-and-package-schema-reference.md)
