if(NOT LITE_WITH_BM)
  return()
endif()

lite_cc_library(subgraph_bridge_utility_bm SRCS utility.cc DEPS)
lite_cc_library(subgraph_bridge_graph_bm SRCS graph.cc DEPS subgraph_bridge_utility_bm)

set(bm_subgraph_bridge_deps subgraph_bridge_registry subgraph_bridge_engine subgraph_bridge_utility_bm subgraph_bridge_graph_bm)

lite_cc_library(subgraph_bridge_act_op_bm SRCS act_op.cc DEPS ${bm_subgraph_bridge_deps})
lite_cc_library(subgraph_bridge_conv_op_bm SRCS conv_op.cc DEPS ${bm_subgraph_bridge_deps})
lite_cc_library(subgraph_bridge_elementwise_ops_bm SRCS elementwise_ops.cc DEPS ${bm_subgraph_bridge_deps})
lite_cc_library(subgraph_bridge_pool_op_bm SRCS pool_op.cc DEPS ${subgraph_bridge_deps_bm})
lite_cc_library(subgraph_bridge_softmax_op_bm SRCS softmax_op.cc DEPS ${subgraph_bridge_deps_bm})
lite_cc_library(subgraph_bridge_mul_op_bm SRCS mul_op.cc DEPS ${bm_subgraph_bridge_deps})
lite_cc_library(subgraph_bridge_batch_norm_op_bm SRCS batch_norm_op.cc DEPS ${bm_subgraph_bridge_deps})
lite_cc_library(subgraph_bridge_scale_op_bm SRCS scale_op.cc DEPS ${bm_subgraph_bridge_deps})

set(bm_subgraph_bridges
        subgraph_bridge_registry
        subgraph_bridge_engine
        subgraph_bridge_graph_bm
        subgraph_bridge_act_op_bm
        subgraph_bridge_conv_op_bm
        subgraph_bridge_elementwise_ops_bm
        subgraph_bridge_pool_op_bm
        subgraph_bridge_softmax_op_bm
        subgraph_bridge_mul_op_bm
        subgraph_bridge_batch_norm_op_bm
        subgraph_bridge_scale_op_bm
        CACHE INTERNAL "bm_subgraph_bridges")
