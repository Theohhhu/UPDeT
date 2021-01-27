 UPDeT
Official Implementation of [UPDeT: Universal Multi-agent Reinforcement Learning via Policy Decoupling with Transformers](https://openreview.net/forum?id=v9c7hr9ADKx) (ICLR 2021 spotlight)

The framework is inherited from [PyMARL](https://github.com/oxwhirl/pymarl). [UPDeT](https://github.com/hhhusiyi-monash/UPDeT) is written in [pytorch](https://pytorch.org) and uses [SMAC](https://github.com/oxwhirl/smac) as its environment.

## Installation instructions

Set up the working environment:

```shell
pip install -r requirements.txt
```

Set up StarCraft II and SMAC:
```shell
bash install_sc2.sh
```

This will download SC2 into the 3rdparty folder and copy the maps necessary to run over.




## Run an experiment

Before training your own transformer-based multi-agent model, there are a list of things to note.

- Currently, this repository supports marine-based battle scenarios. e.g. `3m`, `8m`, `5m_vs_6m`.
- If you are interested in training a different unit type, carefully modify the ` Transformer Parameters` block at  `src/config/default.yaml` and revise the `_build_input_transformer` function in `basic_controller.python`.
- Before running the experiment, check the agent type in ` Agent Parameters` block at `src/config/default.yaml`.
- This repository contains two new transformer-based agents from the [UPDeT paper](https://arxiv.org/abs/1902.04043) including
   - Standard UPDeT
   - Aggregation Transformer

To train a model, run the following commands

```shell
python3 src/main.py --config=vdn --env-config=sc2 with env_args.map_name=5m_vs_6m
```
All results will be stored in the `Results` folder.

## Performance

#### Single battle scenario
Surpass the GRU baseline with:
- [**QMIX**: QMIX: Monotonic Value Function Factorisation for Deep Multi-Agent Reinforcement Learning](https://arxiv.org/abs/1803.11485)
- [**VDN**: Value-Decomposition Networks For Cooperative Multi-Agent Learning](https://arxiv.org/abs/1706.05296)
- [**QTRAN**: QTRAN: Learning to Factorize with Transformation for Cooperative Multi-Agent Reinforcement Learning](https://arxiv.org/abs/1905.05408)

<!--![](https://github.com/hhhusiyi/UPDeT/blob/master/show.png)-->

#### Multiple battle scenarios

Zero-shot generalize to different tasks:

- Result on 7m-5m-3m transfer learning.

<!--![](https://github.com/hhhusiyi/UPDeT/blob/master/show.png)-->

<!--Note: Only **UPDeT** can be deployed to other scenarios without changing the model's architecture.-->

**More details please refer to [this link](https://arxiv.org/abs/1902.04043).**

## Citing UPDeT

If you use UPDeT in your research, please cite the [UPDeT paper](https://arxiv.org/abs/1902.04043).



In BibTeX format:

```tex
@article{hu2021updet,
  title={UPDeT: Universal Multi-agent Reinforcement Learning via Policy Decoupling with Transformers},
  author={Hu, Siyi and Zhu, Fengda and Chang, Xiaojun and Liang, Xiaodan},
  journal={arXiv preprint arXiv:2101.08001},
  year={2021}
}
```

## License

The MIT License
