# CXR-RGB 胸部X光报告生成基准数据集

CXR-RGB 是一个面向医学影像报告生成任务评测的基准数据集，构建基于公开数据集 IU X-Ray，经严格样本筛选与优化而成。该数据集专注于胸部 X 光影像与对应报告的生成任务，共整合47 个高质量样本。

## 一、数据集特点

- **模态**：CXR（胸部 X 光影像）
- **任务**：Report Generation Benchmark（报告生成基准）
- **数据来源**：基于IU X-Ray 数据集精选优化
- **样本数量**：47 个高质量样本
- **筛选标准**：标签中 "1" 的数量 ≥ 4 个
- **数据格式**：JSON + PNG 格式

## 二、数据集结构

### 2.1 文件结构
```
CXR-RGB/
├── images/                    # 影像文件目录
│   ├── CXR1015_IM-0001-1001.png
│   ├── CXR1015_IM-0001-2001.png
│   ├── CXR1015_IM-0013-1001.png
│   ├── CXR1015_IM-0013-2001.png
│   ├── CXR1187_IM-xxxx-1001.png
│   ├── CXR1187_IM-xxxx-2001.png
│   └── ... (47个样本的影像文件)
├── reports.json              # 所有样本的结构化报告
├── labels.json               # 所有样本的14维标签向量
└── metadata.csv              # 数据集元数据信息
```

### 2.2 reports.json 结构（示例）
```json
{
  "ecgen-radiology/1015.xml": {
    "image": [
      "CXR1015_IM-0001-1001",
      "CXR1015_IM-0001-2001",
      "CXR1015_IM-0013-1001",
      "CXR1015_IM-0013-2001"
    ],
    "report": {
      "COMPARISON": "Comparison information here",
      "INDICATION": "Clinical indication and patient information",
      "FINDINGS": "Detailed radiological findings and observations",
      "IMPRESSION": "Radiologist's impression and diagnosis"
    }
  }
}
```

### 2.3 labels.json 结构（示例）
```json
{
  "ecgen-radiology/1015.xml": [1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 0, 0, 1, 0],
  "ecgen-radiology/1187.xml": [1, 0, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1, 0, 0]
}
```

### 2.4 metadata.csv 结构（示例）
```
study_id,report_id,image_files,positive_count,images_count
1015,ecgen-radiology/1015.xml,CXR1015_IM-0001-1001.png,CXR1015_IM-0001-2001.png,...,6,4
1187,ecgen-radiology/1187.xml,CXR1187_IM-xxxx-1001.png,CXR1187_IM-xxxx-2001.png,4,2
```

## 三、数据示例

### 示例 1 - 高质量样本（6 个阳性标签）

**样本 ID**: ecgen-radiology/1015.xml  
**影像文件**: 
- CXR1015_IM-0001-1001.png
- CXR1015_IM-0001-2001.png  
- CXR1015_IM-0013-1001.png
- CXR1015_IM-0013-2001.png

**报告内容**:
```json
{
  "COMPARISON": "None",
  "INDICATION": "65-year-old female, COPD exacerbation, short of breath",
  "FINDINGS": "Streaky and patchy bibasilar opacities, triangular density projected over the heart on the lateral view. No definite pleural effusion seen, no typical findings of pulmonary edema. Stable cardiomediastinal silhouette with normal heart size.",
  "IMPRESSION": "Bibasilar opacities, right greater than left, features suggest a combination of consolidation and atelectasis"
}
```

**标签向量**: [1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 0, 0, 1, 0]  
**标签统计**: 6 个阳性发现

## 四、严格的筛选标准

CXR-RGB 采用 "标签中 1 的数量≥4" 作为高质量样本的核心筛选标准，确保每个样本都具有丰富的临床信息和多方面的异常发现。

## 五、数据集下载

**百度云盘**  
链接: https://pan.baidu.com/s/1cU0WXxJnG8LCE3bCy1JxLA  
提取码: r4aj
