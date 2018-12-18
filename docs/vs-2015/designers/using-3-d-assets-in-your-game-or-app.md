---
title: Používání 3D prostředků ve hře nebo aplikaci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e04f4c82e6f11f2659b4cc65549efb291009b720
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863591"
---
# <a name="using-3-d-assets-in-your-game-or-app"></a>Používání 3D prostředků ve hře nebo aplikaci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento článek popisuje, jak můžete [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ke zpracování 3D prostředků a zahrnout je do sestavení.  
  
 Po použití nástrojů v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] k vytvoření 3D aktiv, je dalším krokem jejich použití ve vaší aplikaci. Ale předtím, než je můžete využít, vaše prostředky nutné transformovat do formátu, který umožní pochopit rozhraní DirectX. Chcete pomoci transformovat prostředky, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] poskytuje upravitelné sestavení pro každý druh prostředku, který může vytvořit. Pokud chcete zahrnout prostředky v sestavení, vše, co musíte udělat, je nakonfigurujte projekt tak, aby používali úpravy v sestavení, přidávat je do vašeho projektu a konfigurovat prostředky k používání správného vlastního sestavení. Poté můžete načíst aktiva do vaší aplikace a použít je vytvořením a vyplněním prostředků DirectX, stejně jako v jiných aplikacích DirectX.  
  
## <a name="configuring-your-project"></a>Konfigurace projektu  
 Před nasazením 3D prostředků ve vašem sestavení, v rámci [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vědět o druzích prostředků, které chcete nasadit. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] již ví o mnoha běžných typech souborů, ale protože pouze určité typy aplikací používat 3D prostředky [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nepředpokládá, že projekt bude vytvářet tyto typy souborů. Poznáte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , že vaše aplikace používá tyto druhy prostředků pomocí *vlastní nastavení sestavení*– soubory, které informují [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jak efektivně zpracovávat různé typy souborů užitečným způsobem –, které jsou k dispozici pro jednotlivé typy prostředků. Protože tyto úpravy jsou použity na základě jednotlivých projektů, je vše, co musíte udělat, přidat vhodné úpravy do projektu.  
  
#### <a name="to-add-the-build-customizations-to-your-project"></a>Chcete-li přidat vlastní sestavení do projektu  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt a klikněte na tlačítko **závislosti sestavení**, **přizpůsobení sestavení**. **Visual C++ soubory vlastního nastavení sestavení** se zobrazí dialogové okno.  
  
2.  V části **dostupné soubory úpravy sestavení**, zaškrtněte políčka, která odpovídají typům aktiv, které chcete použít v projektu, jak je popsáno v této tabulce:  
  
    |Typ prostředku|Název přizpůsobení sestavení|  
    |----------------|------------------------------|  
    |Texturami a obrázky|**ImageContentTask (.targets, .props)**|  
    |3D modely|**MeshContentTask (.targets, .props)**|  
    |Shadery|**ShaderGraphContentTask (.targets, .props)**|  
  
3.  Zvolte **OK** tlačítko.  
  
## <a name="including-assets-in-your-build"></a>Vložení aktiv do vašeho sestavení  
 Teď, když váš projekt ví o různých druzích 3D prostředky, které chcete použít, dalším krokem je určit, které soubory jsou 3D prostředků a které druhy aktiv se.  
  
#### <a name="to-add-an-asset-to-your-build"></a>Přidání prostředků vašeho sestavení  
  
1. V **Průzkumníka řešení**ve vašem projektu otevřete místní nabídku aktiva a klikněte na tlačítko **vlastnosti**. Asset **stránku vlastností** se zobrazí dialogové okno.  
  
2. Ujistěte se, že **konfigurace** a **platformy** vlastnosti jsou nastaveny na hodnoty, které chcete použít pro své změny.  
  
3. V části **vlastnosti konfigurace**, zvolte **Obecné**a poté v mřížce vlastností v rámci **Obecné**, nastavte **typ položky** vlastnost odpovídající obsahu kanálu typu položky. Například soubor obrázku nebo textury, zvolte možnost **kanál obsahu obrazu**.  
  
   > [!IMPORTANT]
   >  Ve výchozím nastavení [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] předpokládá, že mnoho druhů obrazových souborů zařadit pomocí **Image** typ, který je součástí položky [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Proto budete muset změnit **typ položky** vlastnosti každého obrázku, který má být zpracován kanálem obsahu obrázku. Jiné typy obsahu kanálu zdrojové soubory pro 3D modely a vizuálních shaderů grafiky výchozích hodnot **typ položky**.  
  
4. Zvolte **OK** tlačítko.  
  
   Tady jsou tři typy zřetězených položek obsahu a jejich přiřazeného zdroje a výstupní typy souborů.  
  
|Typ položky|Typy zdrojových souborů|Formát výstupního souboru|  
|---------------|-----------------------|------------------------|  
|**Kanál obsahu obrázku**|Formát PNG (.png)<br /><br /> JPEG (JPG, JPEG, JPE, JFIF)<br /><br /> Povrch Direct Draw (.dds)<br /><br /> Graphics Interchange Format (.gif)<br /><br /> Rastr (.bmp, .dib)<br /><br /> Tagged Image File Format (.tif, .tiff)<br /><br /> Targa (TGA)|Povrch DirectDraw (.dds)|  
|**Kanál obsahu mřížky**|Soubor AutoDesk FBX Interchange (.fbx)<br /><br /> Soubor DAE standardu Collada (.dae)<br /><br /> Soubor Wavefront OBJ (obj)|Soubor mřížky 3D (.cmo)|  
|**Kanál obsahu shaderu**|Graf vizuálních shaderů (.dgsl)|Kompilovaný výstup shaderu (.cso)|  
  
## <a name="configuring-asset-content-pipeline-properties"></a>Konfigurace vlastností kanálu obsahu prostředků  
 Vlastnosti kanálu obsahu každého souboru prostředků můžete nastavit tak, aby byl vytvořen určitým způsobem.  
  
#### <a name="to-configure-content-pipeline-properties"></a>Konfigurace vlastností kanálu obsahu  
  
1.  V **Průzkumníka řešení**ve vašem projektu otevřete místní nabídku pro soubor aktiv a klikněte na tlačítko **vlastnosti**. Asset **stránku vlastností** se zobrazí dialogové okno.  
  
2.  Ujistěte se, že **konfigurace** a **platformy** vlastnosti jsou nastaveny na hodnoty, které chcete použít pro své změny.  
  
3.  V části **vlastnosti konfigurace**, vyberte uzel obsahu kanálu – například **obsah kanálu obrazu** pro prostředky textury a obrazu – a v tabulce vlastností nastavte vlastnosti na odpovídající hodnoty. Například, chcete-li generování Mipmap pro textury během sestavení, nastavte **generovat Mips** vlastnost **Ano**.  
  
4.  Zvolte **OK** tlačítko.  
  
### <a name="image-content-pipeline-configuration"></a>Konfigurace zřetězení obrazového obsahu  
 Při použití nástroje obsahu kanálu obrázku k tvorbě prostředku textury můžete komprimovat textury různými způsoby, uvádí, zda by měl být vygenerován v okamžiku sestavení úrovní MIP a změnit název výstupního souboru.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Komprese**|Určuje typ komprese, který se používá pro výstupní soubor.<br /><br /> Dostupné jsou následující možnosti:<br /><br /> -   **Bez komprese**<br />-   **Komprese BC1_UNORM**<br />-   **Komprese BC1_UNORM_SRGB**<br />-   **BC2_UNORM komprese**<br />-   **BC2_UNORM_SRGB komprese**<br />-   **BC3_UNORM komprese**<br />-   **BC3_UNORM_SRGB komprese**<br />-   **BC4_UNORM komprese**<br />-   **Komprese BC4_SNORM**<br />-   **BC5_UNORM komprese**<br />-   **BC5_SNORM komprese**<br />-   **BC6H_UF16 komprese**<br />-   **BC6H_SF16 komprese**<br />-   **BC7_UNORM komprese**<br />-   **BC7_UNORM_SRGB komprese**<br /><br /> Informace o komprimovaných formátech podporovaných různými verzemi rozhraní DirectX naleznete v tématu [programovací Příručka pro DXGI](http://go.microsoft.com/fwlink/p/?LinkId=246265).|  
|Převést na formát přednásobené alfa|**Ano** převést obrázek na formát přednásobené alfa do výstupního souboru; v opačném případě **ne**. Pouze výstupního souboru se změní, zůstává stejná jako zdroje obrázku.|  
|**Generovat Mips**|**Ano** Generovat úplný řetěz MIP v okamžiku sestavení a zahrnout do výstupního souboru; v opačném případě **ne**. Pokud **ne**a zdrojový soubor již obsahuje řetězec mipmap, potom výstupní soubor bude obsahovat MIP řetězec; v opačném případě výstupní soubor nebude mít žádný řetězec MIP.|  
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité:** změna příponu názvu souboru výstupního souboru nemá žádný vliv na formát souboru.|  
  
### <a name="mesh-content-pipeline-configuration"></a>Konfigurace kanálu obsahu mřížky  
 Při použití nástroje mřížka obsahu kanálu k vytvoření mřížky prostředku můžete změnit název výstupního souboru.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité:** změna příponu názvu souboru výstupního souboru nemá žádný vliv na formát souboru.|  
  
### <a name="shader-content-pipeline-configuration"></a>Konfigurace kanálu obsahu shaderu  
 Při použití nástroje shader obsahu kanálu k vytvoření shaderu prostředku můžete změnit název výstupního souboru.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité:** změna příponu názvu souboru výstupního souboru nemá žádný vliv na formát souboru.|  
  
## <a name="loading-and-using-3-d-assets-at-run-time"></a>Načtení a použití 3D aktiv za běhu  
  
### <a name="using-textures-and-images"></a>Používání textur a obrázků  
 Direct3D poskytuje funkce pro vytváření prostředků textur. V Direct3D 11 D3DX11 knihovna nástrojů poskytuje další funkce pro vytváření zdrojů textur a náhledů zdrojů přímo z obrazových souborů. Další informace o tom, jak vytvořit prostředek textury v Direct3D 11 naleznete v tématu [textury](http://go.microsoft.com/fwlink/p/?LinkID=246267). Další informace o tom, jak použít knihovnu D3DX11 k vytvoření zdroje textury nebo náhledu zobrazení z obrazového souboru, naleznete v tématu [jak: Inicializace texturu ze souboru](http://go.microsoft.com/fwlink/p/?LinkId=246268).  
  
### <a name="using-3-d-models"></a>Pomocí 3D modelů  
 Direct3D 11 neposkytuje funkce pro vytváření prostředků z 3D modelů. Místo toho je nutné napsat kód, který čte soubor 3D modelu a vytvoří vertex a index vyrovnávací paměti, které představují 3D model a všechny prostředky, které model vyžaduje – například textury nebo shadery.  
  
### <a name="using-shaders"></a>Používání shaderů  
 Direct3D poskytuje funkce pro vytváření zdrojů shaderu a jejich vazbu na programovatelném grafickém kanálu. Další informace o tom, jak vytvořit prostředek shaderu v Direct3D a jeho vazbu na kanálu, naleznete v tématu [Průvodce programováním pro HLSL](http://go.microsoft.com/fwlink/p/?LinkID=261521).  
  
 V programovatelném grafickém kanálu musí každá fáze kanálu poskytnout další fázi kanálu, který je formátován tak, aby mohli srozumitelně výsledek. Protože Shader Designer může vytvářet pouze pixel shadery, to znamená, že do své aplikace a ujistěte se, že data, která přijímá v očekávaném formátu. Několika fázím programovatelného shaderu před shaderem obrazového bodu a geometrickou transformací – vertex shader, shader trupu, shader domény a shader geometrie. Neprogramovatelná teselace fáze se také projeví před shaderem pixelu. Bez ohledu na to, která z těchto fází přímo předchází pixel shader musí poskytnout výsledek v tomto formátu:  
  
```hlsl  
  
struct PixelShaderInput  
{  
    float4 pos : SV_POSITION;  
    float4 diffuse : COLOR;  
    float2 uv : TEXCOORD0;  
    float3 worldNorm : TEXCOORD1;  
    float3 worldPos : TEXCOORD2;  
    float3 toEye : TEXCOORD3;  
    float4 tangent : TEXCOORD4;  
    float3 normal : TEXCOORD5;  
};  
```  
  
 V závislosti na uzlech návrháře shaderu, které v shaderu používáte budete také muset poskytnutí dalších údajů ve formátu podle těchto definicí:  
  
```  
  
Texture2D Texture1 : register( t0 );  
Texture2D Texture2 : register( t1 );  
Texture2D Texture3 : register( t2 );  
Texture2D Texture4 : register( t3 );  
Texture2D Texture5 : register( t4 );  
Texture2D Texture6 : register( t5 );  
Texture2D Texture7 : register( t6 );  
Texture2D Texture8 : register( t7 );  
  
TextureCube CubeTexture1 : register( t8 );  
TextureCube CubeTexture2 : register( t9 );  
TextureCube CubeTexture3 : register( t10 );  
TextureCube CubeTexture4 : register( t11 );  
TextureCube CubeTexture5 : register( t12 );  
TextureCube CubeTexture6 : register( t13 );  
TextureCube CubeTexture7 : register( t14 );  
TextureCube CubeTexture8 : register( t15 );  
  
SamplerState TexSampler : register( s0 );  
  
cbuffer MaterialVars : register (b0)  
{  
    float4 MaterialAmbient;  
    float4 MaterialDiffuse;  
    float4 MaterialSpecular;  
    float4 MaterialEmissive;  
    float MaterialSpecularPower;  
};  
  
cbuffer LightVars : register (b1)  
{  
    float4 AmbientLight;  
    float4 LightColor[4];  
    float4 LightAttenuation[4];  
    float3 LightDirection[4];  
    float LightSpecularIntensity[4];  
    uint IsPointLight[4];  
    uint ActiveLights;  
}  
  
cbuffer ObjectVars : register(b2)  
{  
    float4x4 LocalToWorld4x4;  
    float4x4 LocalToProjected4x4;  
    float4x4 WorldToLocal4x4;  
    float4x4 WorldToView4x4;  
    float4x4 UVTransform4x4;  
    float3 EyePosition;  
};  
  
cbuffer MiscVars : register(b3)  
{  
    float ViewportWidth;  
    float ViewportHeight;  
    float Time;  
};  
```  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Export textury obsahující mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Popisuje způsob použití obsahu kanálu obrazu pro export textury obsahující předem vypočtené mipmapy.|  
|[Postupy: Export textury s přednásobeným alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Popisuje způsob použití obsahu kanálu obrazu pro export textury obsahující předem vynásobené hodnoty alfa.|  
|[Postupy: Export textury pro použití s rozhraním Direct2D nebo aplikacemi JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Popisuje způsob použití obsahu kanálu obrázku k exportu textur, který lze použít v aplikaci Direct2D nebo JavaScript.|  
|[Práce s 3D prostředky pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Popisuje nástroje pro úpravy, které poskytuje Visual Studio pro vytváření a manipulaci se 3D prostředky, které zahrnují textury a obrázky, 3D modely a shadery.|  
|[Postupy: Exportování shaderu](../designers/how-to-export-a-shader.md)|Popisuje, jak exportovat shader z Návrháře shaderu.|



