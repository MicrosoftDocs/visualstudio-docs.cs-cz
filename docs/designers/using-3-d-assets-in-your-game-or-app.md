---
title: Používání 3D datových zdrojů ve hře nebo v aplikaci
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d38f87970d5f9ff6d90befc61073cc4ed3d4ca92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589822"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>Postup: Použití 3D datových zdrojů ve hře nebo v aplikaci

Tento článek popisuje, jak můžete použít Visual Studio ke zpracování 3D datových zdrojů a zahrnout je do sestavení.

Po použití nástrojů v sadě Visual Studio k vytvoření 3D datových zdrojů je dalším krokem jejich použití v aplikaci. Než je však budete moci použít, musí být vaše datové zdroje transformovány do formátu, kterému rozhraní DirectX rozumí. Visual Studio poskytuje vlastní nastavení sestavení pro každý druh datového zdroje, který může vytvořit, aby vám pomohl transformovat prostředky. Chcete-li zahrnout datové zdroje do sestavení, stačí nakonfigurovat projekt tak, aby používal vlastní nastavení sestavení, přidával datové zdroje do projektu a nakonfiguroval prostředky tak, aby používaly správné přizpůsobení sestavení. Poté můžete prostředky načíst do aplikace a použít je vytvořením a vyplněním prostředků DirectX stejně jako v jakékoli jiné aplikaci DirectX.

## <a name="configure-your-project"></a>Konfigurace projektu

Před nasazením 3D prostředků jako součást sestavení visual studio musí vědět o typech prostředků, které chcete nasadit. Visual Studio už ví o mnoha běžných typech souborů, ale protože pouze určité druhy aplikací používají 3D prostředky, Visual Studio nepředpokládá, že projekt bude vytvářet tyto druhy souborů. Visual Studio můžete říct, že vaše aplikace používá tyto druhy datových zdrojů pomocí *vlastního nastavení*– souborů, které aplikaci Visual Studio sdělují, jak zpracovat různé typy souborů užitečným způsobem – které jsou k dispozici pro každý typ datového zdroje. Vzhledem k tomu, že tato vlastní nastavení jsou použita pro projekt, stačí přidat příslušné vlastní nastavení do projektu.

### <a name="to-add-the-build-customizations-to-your-project"></a>Přidání vlastního nastavení sestavení do projektu

1. V **Průzkumníku řešení**otevřete místní nabídku projektu a pak zvolte **Sestavení závislostí** > **sestavení vlastní nastavení**.

   Zobrazí se dialogové okno **Soubory vlastního nastavení sady Visual C++** .

2. V části **Dostupné soubory vlastního nastavení**zaškrtněte políčka, která odpovídají typům prostředků, které chcete v projektu použít, jak je popsáno v následující tabulce:

    |Typ assetu|Název vlastního nastavení sestavení|
    |----------------| - |
    |Textury a obrázky|**ImageContentTask(.targets, .props)**|
    |3D modely|**MeshContentTask(.cíle, .props)**|
    |Shadery|**ShaderGraphContentTask(.targets, .rekvizity)**|

3. Zvolte tlačítko **OK.**

## <a name="include-assets-in-your-build"></a>Zahrnutí datových zdrojů do sestavení

Nyní, když váš projekt ví o různých typech 3D datových zdrojů, které chcete použít, je dalším krokem zjistit, které soubory jsou 3D datové zdroje a jaké druhy datových zdrojů jsou.

### <a name="to-add-an-asset-to-your-build"></a>Přidání datového zdroje do sestavení

1. V **Průzkumníku řešení**otevřete v projektu místní nabídku datového zdroje a pak zvolte **Vlastnosti**.

   Zobrazí se dialogové okno **Stránka vlastností** datového zdroje.

2. Ujistěte se, že **konfigurace** a **platforma** vlastnosti jsou nastaveny na hodnoty, na které chcete, aby změny použít.

3. V **části Vlastnosti konfigurace**zvolte **Obecné**a potom v mřížce vlastností v části **Obecné**nastavte vlastnost **Type položky** na příslušný typ položky kanálu obsahu. Například pro soubor obrazu nebo textury zvolte **Kanál obsahu obrázků**.

    > [!IMPORTANT]
    > Ve výchozím nastavení Visual Studio předpokládá, že mnoho druhů obrazových souborů by měly být rozděleny do kategorií pomocí typu **položky obrázek,** který je integrován do sady Visual Studio. Proto je třeba změnit vlastnost **Typ položky** každého obrázku, který chcete zpracovat kanálem obsahu bitové kopie. Jiné typy zdrojových souborů kanálu obsahu pro 3D modely a vizuální grafiky shaderu ve výchozím nastavení na správný **typ položky**.

4. Zvolte tlačítko **OK.**

Následují tři typy položek kanálu obsahu a jejich přidružené typy zdrojových a výstupních souborů.

|Typ položky|Typy zdrojových souborů|Formát výstupního souboru|
|---------------| - | - |
|**Kanál obsahu obrázků**|Grafika přenosné sítě (*.png*)<br /><br /> JPEG (*.jpg*, *.jpeg*, *.jpe*, *.jfif*)<br /><br /> Povrch přímého kreslení (*.dds*)<br /><br /> Formát pro výměny grafiky (*.gif*)<br /><br /> Bitmapa (*.bmp*, *.dib*)<br /><br /> Formát souboru označeného obrázkem (*.tif*, *.tiff*)<br /><br /> Targa (*.tga*)|Povrch directdraw (*.dds*)|
|**Kanál obsahu sítě**|AutoDesk FBX Výměnný soubor (*.fbx*)<br /><br /> Soubor Collada DAE (*.dae*)<br /><br /> Wavefront OBJ soubor (*.obj*)|3D soubor sítě (*cmo*)|
|**Kanál obsahu shaderu**|Graf vizuálního shaderu (*.dgsl*)|Zkompilovaný výstup shaderu (*.cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>Konfigurace vlastností kanálu obsahu datových zdrojů

Můžete nastavit vlastnosti kanálu obsahu každého souboru datového zdroje tak, aby byl vytvořen určitým způsobem.

### <a name="to-configure-content-pipeline-properties"></a>Konfigurace vlastností kanálu obsahu

1. V **Průzkumníku řešení**otevřete v projektu místní nabídku souboru datových zdrojů a pak zvolte **Vlastnosti**.

   Zobrazí se dialogové okno **Stránka vlastností** datového zdroje.

2. Ujistěte se, že **vlastnosti Konfigurace** a **Platforma** jsou nastaveny na hodnoty, které chcete, aby se změny vztahovaly.

3. V části **Vlastnosti konfigurace**zvolte uzel kanálu obsahu (například **Kanál obsahu obrázků** pro prostředky textury a obrazu) a v mřížce vlastností nastavte vlastnosti na příslušné hodnoty. Chcete-li například generovat mipmapy pro datový zdroj textury v době sestavení, nastavte vlastnost **Generate Mips** na **Ano**.

4. Zvolte tlačítko **OK.**

### <a name="image-content-pipeline-configuration"></a>Konfigurace kanálu obsahu obrázku

Použijete-li nástroj pro vytváření prostředků textury pomocí nástroje pro kanál obsahu bitové kopie, můžete texturu komprimovat různými způsoby, určit, zda mají být úrovně MIP generovány v době sestavení, a změnit název výstupního souboru.

|Vlastnost|Popis|
|--------------|-----------------|
|**Komprimovat**|Určuje typ komprese, který se používá pro výstupní soubor.<br /><br /> Dostupné jsou tyto možnosti:<br /><br /> -   **Žádná komprese**<br />-   **BC1_UNORM komprese**<br />-   **BC1_UNORM_SRGB komprese**<br />-   **BC2_UNORM komprese**<br />-   **BC2_UNORM_SRGB komprese**<br />-   **BC3_UNORM komprese**<br />-   **BC3_UNORM_SRGB komprese**<br />-   **BC4_UNORM komprese**<br />-   **BC4_SNORM komprese**<br />-   **BC5_UNORM komprese**<br />-   **BC5_SNORM komprese**<br />-   **BC6H_UF16 komprese**<br />-   **BC6H_SF16 komprese**<br />-   **BC7_UNORM komprese**<br />-   **BC7_UNORM_SRGB komprese**<br /><br /> Informace o tom, které formáty komprese jsou podporovány v různých verzích rozhraní DirectX, naleznete v [tématu Programming Guide for DXGI](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews).|
|Převést na předem vynásobený alfa formát|**Ano,** chcete-li převést obraz na předem vynásobený alfa formát ve výstupním souboru; jinak **ne**. Změní se pouze výstupní soubor, zdrojový obraz se nezmění.|
|**Generovat Mips**|**Ano** generovat úplný řetězec MIP v době sestavení a zahrnout jej do výstupního souboru; jinak **ne**. Pokud **ne**a zdrojový soubor již obsahuje řetězec mipmap, bude mít výstupní soubor řetězec MIP; v opačném případě bude výstupní soubor mít žádný řetězec MIP.|
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité:**  Změna přípony názvu souboru výstupního souboru nemá žádný vliv na jeho formát souboru.|

### <a name="mesh-content-pipeline-configuration"></a>Konfigurace kanálu obsahu sítě

Když použijete nástroj pro vytváření datového zdroje obsahu sítě, můžete změnit název výstupního souboru.

|Vlastnost|Popis|
|--------------|-----------------|
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité:**  Změna přípony názvu souboru výstupního souboru nemá žádný vliv na jeho formát souboru.|

### <a name="shader-content-pipeline-configuration"></a>Konfigurace kanálu obsahu shaderu

Použijete-li k vytvoření datového zdroje shaderu nástroj pro kanál obsahu shaderu, můžete změnit název výstupního souboru.

|Vlastnost|Popis|
|--------------|-----------------|
|**Výstup obsahu**|Určuje název výstupního souboru. **Důležité:**  Změna přípony názvu souboru výstupního souboru nemá žádný vliv na jeho formát souboru.|

## <a name="load-and-use-3d-assets-at-run-time"></a>Načítání a používání 3D datových zdrojů za běhu

### <a name="use-textures-and-images"></a>Použití textur a obrázků

Direct3D poskytuje funkce pro vytváření prostředků textury. V direct3D 11 poskytuje knihovna nástrojů D3DX11 další funkce pro vytváření prostředků textury a zobrazení prostředků přímo ze obrazových souborů. Další informace o tom, jak vytvořit prostředek textury v Direct3D 11, naleznete v [tématu Textury](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures). Další informace o použití knihovny D3DX11 k vytvoření prostředku textury nebo zobrazení prostředků ze souboru obrázku naleznete v [tématu Jak: Inicializovat texturu ze souboru](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to).

### <a name="use-3d-models"></a>Použití 3D modelů

Rozhraní Direct3D 11 neposkytuje funkce pro vytváření prostředků z 3D modelů. Místo toho musíte napsat kód, který přečte soubor 3D modelu a vytvoří vyrovnávací paměti vrcholů a indexů, které představují 3D model a všechny prostředky, které model vyžaduje – například textury nebo shadery.

### <a name="use-shaders"></a>Použití stínidla

Direct3D poskytuje funkce pro vytváření prostředků shaderu a jejich vazbu na programovatelný grafický kanál. Další informace o tom, jak vytvořit prostředek shaderu v Direct3D a svázat ho s kanálem, naleznete [v tématu Programming Guide for HLSL](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide).

V programovatelné grafické kanálu každé fázi kanálu musí poskytnout další fázi kanálu výsledek, který je formátován tak, aby mu porozumět. Vzhledem k tomu, že návrhář shaderu shaderu shaderů může vytvářet jenom shadery pixelů, znamená to, že je na vaší aplikaci, aby zajistila, že data, která obdrží, budou ve formátu, který očekává. Před shaderem obrazových bodů dochází k několika programovatelným fázím shaderu a provádějí geometrické transformace – shader vrcholů, shader trupu, shader domény a shader geometrie. Neprogramovatelná fáze mozaikování se také vyskytuje před shaderem obrazových bodů. Bez ohledu na to, která z těchto fází přímo předchází shaderu obrazových bodů, musí poskytnout svůj výsledek v tomto formátu:

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

V závislosti na uzlech Návrhář shaderu, které používáte v shaderu, může být také vhodné zadat další data ve formátu podle těchto definic:

```hlsl
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

|Nadpis|Popis|
|-----------|-----------------|
|[Postup: Export textury, která obsahuje mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|Popisuje, jak pomocí kanálu obsahu obrázků exportovat texturu, která obsahuje předem vypočítané mipmapy.|
|[Postupy: Export textury s přednásobeným alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|Popisuje způsob použití kanálu obsahu obrázků k exportu textury, která obsahuje předem vynásobené hodnoty alfa.|
|[Postup: Export textury pro použití s aplikacemi Direct2D nebo JavaScript](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|Popisuje, jak pomocí kanálu obsahu obrázků exportovat texturu, kterou lze použít v aplikaci Direct2D nebo JavaScript.|
|[Práce s 3D datovými zdroji pro hry a aplikace](../designers/working-with-3-d-assets-for-games-and-apps.md)|Popisuje nástroje pro úpravy, které sada Visual Studio poskytuje pro vytváření a manipulaci s 3D datovými zdroji, mezi něž patří textury a obrazy, 3D modely a stínidla.|
|[Postupy: Export shaderu](../designers/how-to-export-a-shader.md)|Popisuje způsob exportu shaderu z návrháře shaderu.|
